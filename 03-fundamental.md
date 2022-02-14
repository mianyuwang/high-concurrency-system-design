# 03: System design objective I: How to improve performance

## Three design objectives of high concurrency systems

High concurrency design aims to design the system to handle more concurrency requests hence undergo more traffic.

- High performance reflects the user experience, imagine two systems which undergo 10,000 qps, one responds in milli seconds vs. the other one responds in seconds.
- High availability reflects the time the system serving the users normally, imagine a system operating 24/365 without down time vs. the other one always under maintenance.
- High scalability means the system can be easily scaled out to handle peak traffic in a short amount of time.

## Principle of performance optimization

- Problem oriented: Do not optimize in the early stage to complicate the design and waste time to market.
- 80-20 rule: Use 20% of effort to solve 80% of performance problem, so prioritize your work for the main bottleneck.
- Data driven: Measure optimization results by metrics.
- This is a continuous process.

## Quantified metrics of performance

- Average Response Time: Response time of a given period of time. The issue of average is it is not sensitive to the underlying performance change. We often use it as a reference.
- Maximum Response Time: The issue of maximum is it is too sensitive.
- Percentile: For example, 75, 90, 95 percentile, the higher percentile, the more sensitive to the slow requests. It is more suitable as statistics for response time.

We often use **throughput** and **response time** to measure concurrency, they are reciprocal. Our performance optimization objective is usually like _make 99 percentile of response time below 10 ms in 10,000 qps throughput_.

From user experience perspective, users won't feel any obvious latency under 200ms, and will feel latency under 1s but it is acceptable. So a typical healthy system wants 99 percentile under 200ms and 99.99% requests should be below 1s.

## Optimization under high concurrency

If you have a system with one core and response time is 10ms to execute a task, the throughput is then 100/s. How do we improve the concurrent processing capability?

### Raise the processing cores

Amdahl’s law: acceleration ratio is `1/(1-p+p/s)`, where `s` is the count of parallel processes, `p` is the ratio in the task can be parallel.

We can't increase the parallel processes forever, when utilization is saturated, we will hit a critical point and even see the performance deterioration.

### Reduce the response time of a single task

Understand the task is CPU bound or I/O bound task, use various tools to identify the bottleneck.

For CPU bound tasks, we can choose a more efficicent algorithm or reduce computation by profiling and locating the most expensive module or function.

For I/O bound tasks means the most operations are waiting for I/O like disks or network. We usually leverage some tools or monitoring to locate the bottleneck, and adopt different solutions according the issue.
