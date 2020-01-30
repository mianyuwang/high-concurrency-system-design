# High Concurrency System Design

Introduction
===============

Why do we care about high concurrency system design?
----------------------------------------------------

Before answering that, let us think about the following problems.
- In Instgram, a celebrity is having millions or hundreds of millions followers. How can you make sure her new post can be viewed by all followers in real time?
- During Black Friday, when thousands of buyers are rushing for a deal, how to make sure this product won't be oversold?

Those problems are the common pain points when you design and implement  distributed systems, all involving how to achieve high availability and high performance in a high concurrency scenario. Knowing how to tackle these problem, you can deliver better user experience to your clients and grow your technical skills.

Chapter 1: High concurrency system: What is the general design strategy?
========================================================================

We all know high concurrency indicates huge volumes or flows of user requests and data. The solution we are seeking is more like controlling flows so that they can be processed by services and components in the system in a stable way.

We handle huge volumes of requests similar to handling flooding in three general strategies.
- *Scale-out*: Divide and conque is a common strategy, which distributes the flow to multiple servers, each handles a small portion of volumes.
- *Cache*: Use cache to improve the system performance, like widening the river so that more requests can flow at the same time.
- *Async*: For some scenarios, we can return the requests before we actually process them, then notify the origin when processing is done. In this way, more requests can flow at the same time as well.
