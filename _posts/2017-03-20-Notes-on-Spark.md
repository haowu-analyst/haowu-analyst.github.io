---
layout: post
title: "Some notes on Spark official documentation"
date: 2017-03-20
category: scribble
---
I write these down to help myself memorise things better.

#### Cluster Mode Overview
* Spark applications run as independent sets of processes on a cluster.
* The application's *main* program is the driver program. The `SparkContext` in the main program coordinates the processes.
* Three types of *cluster managers*:
  - Spark standalone
  - Mesos
  - YARN
* A *cluster manager* manages the nodes in the cluster. Spark gets *executors* from the cluster manager.
* The `SparkContext` makes sure code (`.jar` or `.py`) and data are synced over the executors/nodes. It then run *tasks* on the executors.
* Each application gets its own executor processes. Tasks from different applications run in different JVMs. 
* Data can only be shared between applications by writing/reading from external storage (disk).
* The driver program lives on the driver node. It must listen for and accept incoming connections from its executors.
* It's good to have the driver node as close to the worker nodes as possible.
* The application jar (or .py) should be built with reference to the correct version of Spark, Scala (or Python) and hadoop. However, it should not directly include Spark or Hadoop libraries, which are added at runtime.
* The application's only driver program creates the applications `SparkContext` and runs the applications only main() function to enter the application.
* The *deploy mode* determines where the driver program is run, inside or outside of the cluster.
* An executor process is launched for every node the application asked for from the cluster manager.
* A job is one end-to-end execution of the application on the cluster. It consists of multiple tasks, often divided into stages and are executed in parallel.

