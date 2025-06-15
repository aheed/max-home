---
title: "Object pooling"
excerpt: ""
featuredImage: "./images/recycle.svg"
publishDate: "2025-06-15"
publish: true
categories: ["Tech", "Progress", "Unity"]

seo:
  title: ""
  description: ""
  image: "./images/discussing_the_Dambusters_Raid.jpg"
---

# Object pooling

## The problem
Instantiating and activating game objects (enemy tanks, tress etc) is costly. It takes a lot of CPU time. Frame rate suffers.
Keeping many game objects alive at the same time may consume a lot of memory and CPU.

## Non-solutions
The nature of the game presents a challenge: There is not a fixed level size. New airfields and random enemies keep materializing indefinitely. Therefore it is not possible to prepopulate the scene with objects at level start.

Parallelization is not an option because of lack of support for it in WebGL builds.

Instantiating and destroying objects continuously is certainly possible, but with dozens of objects per second it becomes a performance problem.

## Helicopter view solution
Keep pools of objects and reuse as needed. An enemy tank scrolled out of view at bottom of the screen is reused by changing it's position. Next second it could scroll into view again from the top. Changing a game object's position is way cheaper than destroying and constructing objects.

## Challenges

### Start() vs custom respawn function
Object initialization typically takes place in the special function **Start**, which is automatically called before first Update call after instantiation. With pooling this is not enough anymore. An object may need to be reinitialized when reused.

For example, an enemy tank that was hit changed its appeared to a burnt-out wreck, then returned to its object pool. When reusing the instance the tank's appearance must go back to its shiny new menacing appearance.

### Double release
Accidentally releasing an object (putting it back into an object pool) while it is already in the pool could cause nasty bugs. Compare to the non-pooled case: **Destroy()** can be called on an already destroyed game object without errors.

It's probably a good idea to add some safety feature to avoid/detect double releases. **ObjectPool&lt;T&gt;** (see below) does have a CollectionCheck feature, but you must not forget to turn that off when your solution is somewhat mature. It linear searches the whole pool on every release!!! Potentially devastating for performance.

### Coupling
Choosing an object lifetime managing strategy may have a big impact on a lot of code in your project. This will most likely apply to both the implementations of pooled classes and other code. Changing object lifetime strategy could become costly and, as usual, it is hard to know the optimum strategy at an early project stage.

## Best practices
Unity does provide a C# generic **ObjectPool&lt;T&gt;** and an interface **IObjectPool&lt;T&gt;**.

This is a good start but there are still some challenges with recycling pooled objects. You can not just call **Destroy(mytank)** on a pooled game object (**mytank** in this case). Instead the object must be corraled back to its pool. Something like `mypool.Release(mytank)`. This should preferrably be done without a strong coupling between caller and pool implementation/instance.

Unity also provides an accompanying wrapper generic, **PooledObject&lt;T&gt;**. It implements **IDisposible** and contains a reference to the object's pool.
**PooledObject&lt;T&gt;** still doesn't solve the object suicide use case: An enemy tank detects it's been hit by a bomb and should therefore disappear from view and go back to its pool. The problem is it does not know about it's wrapping PooledObject instance.

## Requirements

1. Object suicide shall be supported.
2. Any double release shall be impossible or at least should be detected immediately if it happens.
3. A managed object implementation shall not have to be aware of its pool type.
4. It shall be easy to change pool types.
5. Deactivating a pooled object instance (turn off active behaviors to save CPU) on release to its pool shall be supported in a uniform way.
6. Resetting a pooled object instance to its original state (turn burned out tank back into shiny new tank) on reuse shall be supported in a uniform way.


## Solution

**ManagedObjectReference** serves the same purpose as the standard generic **PooledObject&lt;T&gt;** but it also ensures a managed object can not be double released.

**ManagedObject** is a **MonoBehaviour** derived base class for poolable game object types. It keeps a **ManagedObjectReference** member which enables object suicide and decouples a **ManagedObject** derived class implementation from the actual pool used to manage its instances.

**ObjectManager** is a class wrapping **ObjectPool&lt;ManagedObject&gt;**.

### Possible improvements
**ObjectManager** and **ManagedObjectReference** could be generics. This would add extra type safety for **ManagedObject** derived classes and associated object pools.
