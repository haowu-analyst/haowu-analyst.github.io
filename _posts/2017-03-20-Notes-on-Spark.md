---
layout: post
title: "Some notes on Spark official documentation"
date: 2017-03-20
category: scribble
---
I write these down to help myself memorise things better.

### Cluster Mode Overview
* Spark applications run as independent sets of processes on a cluster.
* The application's *main* program is the driver program. The `SparkContext` in the main program coordinates the processes.
