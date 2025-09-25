Design of a server farm using queueing theory and simulation
============================================================


In this lab, we want to use SimPy and queueing models to determine the best design for a server farm.

The learning goals of this lab are:

- to apply queueing models such as M/M/1 and M/M/c to a real-world system,
- to write SimPy simulation models,
- to understand the performance characteristics of the different queueing models.

> [!NOTE]
> Document your findings and results in a report. Use the file `Report.md` as a template. You can write it in English or French.


Problem description
-------------------

A company is developing a web application that is expected to have a high load. The company wants to design an efficient server farm to handle the incoming requests. Your task is to analyze and compare different designs for the server farm using queueing theory and discrete-event simulation.

The company has bought a server with a CPU cores. How can they get the best performance for their money? 

The performance metrics to evaluate are:

- the maximum throughput (requests per second),
- the response time (time to handle a request): mean value and 99th percentile


### Assumptions

- There are many independent users sending requests to the web application.
- Measurements have shown that the service times are exponentially distributed. The mean service time depends on the server type.


Option 1: horizontal scaling using Docker Compose
-------------------------------------------------

In order to keep the software simple, the company decides to implement it as a single-threaded application. It creates a Docker Compose configuration with 8 identical containers, and allocates one CPU core per container. Each container can thus handle a single request at a time. A load balancer distributes the incoming requests in a round-robin fashion to the containers.

Measurements have shown that the mean service time for a request on container is 0.1 seconds.

Develop a SimPy simulation model for this option. Document your findings and results in the report.


Option 2: thread-pool for handling multiple requests
----------------------------------------------------

In this option, the company still keeps the software simple as a single-threaded application. However, instead of using Docker Compose, it handles the requests using a thread-pool with 8 threads. The server can thus handle up to 8 requests in parallel. The operating systems mananges the incoming HTTP requests and assigns the requests to the next available thread.

The entire system again runs on the server with 8 CPU cores. Each thread is allocated one CPU core. Since the software and hardware are the same as in option 1, the mean service time for a request is again 0.1 seconds.

Develop a SimPy simulation model for this option. Document your findings and results in the report.


Option 3: parallel processing
-----------------------------

If it helps to reduce the response time, the company is willing to develop a more complex software. The algorithm can be parallelized and run on 8 cores in parallel. In that case the mean service time for a request is reduced to 0.1 seconds / 8 =  0.0125 seconds.

Again, the entire system runs on the server with 8 CPU cores. Each request is thus handled 8 times faster, but the server can only handle a single request at a time.

Develop a SimPy simulation model for this option. Document your findings and results in the report.


Option 4: adding an old server
------------------------------

In addition to the fast 8-core server, the company has an old 1-core server. It considers adding this old server as a second server to option 3. The old server can only handle a single request at a time, and has a mean service time of 0.5 seconds.

The company wants to know if this configuration can improve the throughput and the response time.

You should be able to reuse your simulation models from options 1-3 with the following assumptions:

- The fast server handles 8/9 of the incoming requests, the small server 1/9 of the requests.
- You can combine the metric using the same weights (8/9 and 1/9).

Document your findings and results in the report.
