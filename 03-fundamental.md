# 03: System design objectives: How to improve performance

## 3 design objectives of high concurrency systems

High concurrency design aims to design the system to handle more concurrency requests hence more traffic.

- High performance reflects how quickly the system responds.
- High availability reflects the reliability of the system.
- High scalability means the system can be easily scaled out to handle peak traffic in a short amount of time.

## Principle of optimization

- Problem oriented: Do not optimize in the early stage to complicate the design.
- 80-20 rule: Use 20% of effort to solve 80% of performance problem.
- Data driven: Measure optimization results by metrics.
- This is a continuous process.

## Metrics of performance

- Average
- Maximum
- Percentile

## Optimization under high concurrency

If you have a system with one core and response time is 10ms to execute a task, the throughput is then 100/s. How do we improve the concurrent processing capability?

### Raise the processing cores

We can't increase the parallel processes forever, when utilization is saturated, we will hit a threshold and even see the performance deterioration.

### Reduce the response time of a single task

Understand the task is CPU bound or I/O bound task, use various tools to identify the bottleneck.
