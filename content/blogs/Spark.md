---
title:  "From Concept to Execution: Understanding Apache Spark's Evolution"
date: 2023-09-24T16:21:49+01:00
draft: false
layout: home
---

<div style="text-align: justify;">

_Apache Spark has become a powerhouse in the world of big data processing. It's a tool that has revolutionized the way we handle massive datasets, enabling faster and more efficient data processing and analysis. But where did Spark come from, and how did it evolve into the robust framework we know today? In this blog post, we'll take a journey through the history of Apache Spark, exploring its origins and its remarkable evolution from concept to execution._

## Table of Contents
- [The Birth of Apache Spark](#the-birth-of-apache-spark)
- [Unleashing Spark's Superpowers](#unleashing-sparks-superpowers)
- [Spark Execution](#spark-execution)
   - [Resource Management](#resource-management)
   - [Spark Job Components](#spark-job-components)
   - [Spark Job Submission Workflow](#spark-job-submission-workflow)
- [Conclusion](#conclusion)

## The Birth of Apache Spark 🌟 {#the-birth-of-apache-spark}

Apache Spark's journey began in 2009 at UC Berkeley with the advent of Mesos. At that time, the Apache Hadoop ecosystem lacked the YARN resource manager, which led to the inception of a remarkable class project AMPLab. Their audacious goal: to build a cluster management framework.

### The Emergence of Mesos 🚀

In the year 2009, the emergence of Mesos marked a pivotal moment in the realm of distributed systems. It was conceived to orchestrate the execution and management of distributed applications, offering a promising alternative to traditional approaches.

### Spark: A Testing tool for Mesos 🧠

It was within this innovative environment that Apache Spark was born, Apache Spark conceived initially as a tool to test the capabilities of Mesos. During this period, the dominant paradigm revolved around MapReduce, a model heavily reliant on disk storage. MapReduce's limitations in terms of performance were evident.

But Spark was different, It embraced a memory-centric framework, where the majority of operations occurred within the realm of memory. This strategic shift was a deliberate response to the constraints that had long plagued the MapReduce model.

### The Remarkable Reawakening 💡

However, after its initial inception as a Mesos testing tool, Spark briefly faded into the background, perceived merely as a subproject with a specific purpose—testing Mesos 😔. 

But in 2011, something remarkable happened. The world took notice as it became evident that Spark had achieved a significant breakthrough in performance. It outpaced MapReduce by a wide margin, thanks to its unique in-memory execution model. 🚀

### Apache Spark Takes Flight 🎉

In 2012, Apache Spark officially ascended to the status of an Apache project, solidifying its position as a revolutionary framework in the world of big data processing. 
## Unleashing Spark's Superpowers 🚀 {#unleashing-sparks-superpowers}

Apache Spark, like a superhero in the world of big data, boasts several incredible strengths that set it apart:

### A Unified Stack 🧩
![Unified Stack](https://www.oreilly.com/api/v2/epubs/9781492050032/files/assets/lesp_0103.png)
<!-- <center><i <center><i style="color: gray;">Apache Spark's Unified Stack</i></center>  -->
Spark's unified stack brings together a multitude of data processing and analytics tools under one roof. Whether it's batch processing, real-time stream processing, machine learning, or graph processing, Spark's got it covered. This seamless integration of various data processing tasks makes Spark a true powerhouse.

### Multilingual API Support 🌐

Spark speaks the language of developers! It offers APIs not just in its native Scala but also in Python, Java, and other languages. This multilingual support ensures that developers can work with Spark using the language they're most comfortable with, making it an inclusive and versatile choice.

### Memory-Based Speed 

Spark's brilliance doesn't stop there; Unlike traditional models that rely heavily on disk storage, Spark operates predominantly in-memory. This memory-centric approach results in lightning-fast data processing and analysis, transforming the landscape of big data.

## Spark Execution {#spark-execution}
### Resources Management  💼 {#resource-management}
1. **On a Single Machine:**

   - In a single-machine environment, we have computing resources (CPU, RAM, GPU...) along with an operating system (OS) and multiple applications, as mentioned in the figure below.
   - The (OS) is responsible for resource management, which includes tasks such as resource scheduling and determining the allocation of resources (CPU, Memory, etc...) to individual applications. The allocation is based on available computing resources and the concurrent applications running on your computer.
   <center><img src="/single_machine.png" width="300" height="400"></center>    

2. **In a Cluster:**

   - In a cluster, multiple working nodes are interconnected to form a cohesive computing environment. These nodes collaborate to perform distributed data processing tasks efficiently.
    ![Cluster Setup](/cluster_setup.png)  
   - In a cluster, there are dedicated applications for resource management that orchestrate the allocation of resources, These applications include:
     - Cluster manager
     - Node manager
     <center><img src="/node_cluster_manager.png" width="900" height="200"></center> 

### Spark job components {#spark-job-components}
To run your spark application in a cluster, you have to ask the cluster manager for the needed resources allocation. 🧙‍♂️ It's the **application master**'s duty to ensure you get the resources you need. This "middleman" serves as the entry point to the cluster, making it all happen.

Running a Spark application in a cluster involves the following key components:
1. **Spark application:**

   Each application running on the cluster has its own Application Master. The Application Master is responsible for negotiating resources with the Resource Manager, managing the application's lifecycle, and ensuring that the application gets the resources it needs.  

2. **Spark driver process:**

   - Breaks down the Spark app logic into smaller tasks.
   - Distributes and schedules the work among Spark executors.
   - Tracks the status of all the Spark executors and monitor their progress
   > **Note:** If an executor crashes, it's the driver process that requests the cluster manager for additional resources 🚒.

3. **Spark executor processes:**

   - Execute the tasks assigned by the Spark driver process.
   - Report their status back to the Spark driver 

### Spark Job Submission Workflow {#spark-job-submission-workflow}

![Cluster Setup](/spark_job_workflow.png) 
The above image illustrates the ⚙️ smooth process of Spark job submission:

1. You submit your Spark application to Master Node that interacts with the cluster manager and requests it to take charge of it and manage it.
> **Note:** Master node refers to the node where you submit your Spark application. 

2. The Spark driver process needs to be started, so the cluster manager will request the node manager to start the driver process with the configuration we have specified during app submission.
> If node manager has enough resources, then the Spark driver process will be created 🚀 .

3. The Spark driver process will request the cluster manager for additional resources to allocate resources for executor processes. 

4. The cluster manager will request the node managers to create the executor processes, the node manager will create the executor process if it has enough resources.
> **Note:** The node managers that have created executors send informations about their locations... to the cluster manager 📡. 

5. The cluster manager inform back the driver process about the location of executor processes 📣. 

6. Now, the Spark application is running and the Driver process starts to distribute tasks among the executors. 
> **Note:** All the Spark application logic will be sent to executors in the form of tasks to do the computation in parallel, so the spark driver process is the heart  of spark app. 


This orchestrated flow ensures that your Spark job is executed efficiently within the cluster.

## Conclusion {#conclusion}

Exploring Apache Spark's history has revealed its innovative origins and the 'why' behind its existence 🌱.  Understanding its origins provides a deeper appreciation for the impact it has on the world of data processing. In this article, we've tried to cover essential aspects of Apache Spark, from its history to its submission workflow. I hope you've found this article both informative and insightful, if you have any questions or comments, please reach me out. Thanks for reading!<br><br><br>  

<div style="display: inline-block; background-color: #f0f0f0; border: 1px solid #ccc; padding: 4px 8px; border-radius: 4px;">
  <span style="font-weight: bold;">Apache </span>
</div>
<div style="display: inline-block; background-color: #f0f0f0; border: 1px solid #ccc; padding: 4px 8px; border-radius: 4px;">
  <span style="font-weight: bold;">Spark</span>
</div>
<div style="display: inline-block; background-color: #f0f0f0; border: 1px solid #ccc; padding: 4px 8px; border-radius: 4px;">
  <span style="font-weight: bold;">Mesos</span>
</div>
<div style="display: inline-block; background-color: #f0f0f0; border: 1px solid #ccc; padding: 4px 8px; border-radius: 4px;">
  <span style="font-weight: bold;">Data</span>
</div>


</div>
