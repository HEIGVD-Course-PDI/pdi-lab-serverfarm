Lab report: Design of a server farm using queueing theory and simulation
========================================================================

> [!NOTE]
> Write your report in this document. You can write it in English or French


Traffic model (2p)
------------------

Describe which traffic model you use to model the incoming requests. Justify your choice.


Evaluation of the options 1-3 (3x 9p)
-------------------------------------

Document your findings are results here. In particular, for each option, answer the following questions:

1. Which queueing model do you use to model this option? Justify your choice. (2p)
2. What is the maximum throughput of this option (requests per second)? (1p)
3. Show a plot of the mean and 99th percentile of the response time as a function of the utilization (from 0.1 to 0.9). (3p)
4. What are the numeric values of the mean and 99th percentile of the response time at for low (rho=0.1), medium (rho=0.5), and high (rho=0.9) utilization? (3p)


Evaluation of option 4 (14p)
----------------------------

Document your findings are results here. In particular, answer the following questions:

1. Which queueing model do you use to model this option? Justify your choice. (2p)
2. Can adding the old server improve the maximum throughput? Justify your answer. (1p)
3. How can you compute the mean response time for this option? (1p)
4. How can you compute the 99th percentile of the response time for this option? **This is difficult!** You can use the fact that the response times on each server have an exponential distribution, with $\lambda = 1/mean_response_time$. If you know the means, you can generate random samples from the two distributions, combine them using the weights 8/9 and 1/9, and then compute the 99th percentile of the combined samples. (2p)
5. Show a plot of the mean and 99th percentile of the response time as a function of the utilization (from 0.1 to 0.9). (1p)
6. What are the numeric values of the mean and 99th percentile of the response time at for low (rho=0.1), medium (rho=0.5), and high (rho=0.9) utilization? (3p)
7. Compare the mean response time to option 3. Is it better or worse? Explain your findings. (1p)
8. Compare the 99th percentile to option 3. How can these values be explained? (2p)
9. Is there a scenario where adding the old server is useful? (1p)


Recommendation (5p)
-------------------

Based on your findings, which option would you recommend to the company? (2p)

Besides the best solution, could the other options be useful in some scenarios? (3p)


Conclusion (4p)
---------------

Describe what you have learned about designing server farms. (2p)

Describe a case where 99th percentile have been useful in this lab. (2p)
