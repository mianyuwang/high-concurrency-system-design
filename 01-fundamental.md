# 01: High concurrency system: What is the general design strategy?

We all know high concurrency indicates huge volumes or flows of user requests and data. The solution we are seeking is more like controlling flows so that they can be processed by services and components in the system in a stable way.

We handle huge volumes of requests similar to handling flooding in three general strategies.

- _Scale-out_: Divide and conque is a common strategy, which distributes the flow to multiple servers, each handles a small portion of volumes.
- _Cache_: Use cache to improve the system processing speed, like widening the river so that more requests can flow at the same time.
- _Asynchronous_: For some scenarios, we can return the requests before we actually process them, then notify the origin when processing is done. In this way, more requests can flow at the same time as well.

## Scale-up vs Scale-out

We call the solutions leveraging more powerful CPU and hardware _scale-up_, while the solutions leveraging multiple CPUs or multi-core _scale-out_. They are totally different ideas.

- Scale-up improves the concurrency processing power by purchasing better hardware. For example, the current 4-core 4GB system can handle 200 requests per second, what if we want to handle 400 requests per second? That is simple, go buy a 8-core 8GB machine.

- Scale-out builds a distributed cluster by adding more machines with the same specifications. For the same example above, we will add another 4-core 4GB machine to handle 400 requests per second.

When to choose scale-up and when to choose scale-out? In general, we will prefer scale-up in the beginning because it is simple enough, but when the load exceeds the limit of a single machine, we will have to scale out. However it will introduce new challenges. How to ensure availability whe some nodes are down? How to ensure the consistency when we need to sync up the states among multiple nodes? How to add and remove nodes transparently? Those are all problems we will focus later in this work.

## Improve performance using cache

Cache is originally referring to load data from memory instead of disk, where the average seek time can be reduced from 10ms to ns. Nowadays, any middleware which can reduce the latency we can call it cache.

## Asynchronous processing

Synchronous vs Asynchronous: In sync function invocation, the caller of sync function is blocked until the execution is done, while the caller gets return immediately for an async function and get results through callbacks or event notifications.
