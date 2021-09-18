# Spark-examples

- [Spark-examples](#spark-examples)
  - [Spark general concepts](#spark-general-concepts)
    - [DataFrames](#dataframes)
  - [Running Spark](#running-spark)


## Spark general concepts
Spark Applications consist of a *driver* process and set of *executor* processes.
The driver process runs your *main()* function, sits on a note in the cluster, and is responsible for three things:
1. maintaining information about the Spark Appliction;
2. responding to a user's program or input;
3. analyzing, distributing, and scheduling work across the executors;

A cluster of computers, pools the resources of many machines together, giving the ability to use all the cumulative resources as if they were a single computer. A node is an element of the cluster.

The *executors* are responsible for carrying out the work that the driver assigns them. Each executor is responsible for two things:
1. executing code assigned to it by the driver;
2. reporing the state of the computation on that executor back to the driver node;

Spark session is an object that sits on the executor's JVMs and available to the user through API.

There are two level of API's
* the low-level "unstructured" APIs;
* the higher-level "structured" APIs;

### DataFrames

A DataFrame is the most common Structured API and simply reperesents a talbe of data with rows and collumns.
>Spark has several core abstracitons: Datasets, DataFrames, SQL Tables, and Resilient Distributed Datasets (RDDs).

The list that defines the columns and the types within those collumns is called the *schema* (A Spark DataFrame could span thousands of computers).

__In Spark The core data structures are *immutable*__

```Scala
val myRange = spark.range(1000).toDF("number")
val divisBy2 = myRange.where("number % 2 == 0")
divisBy2.show()
divisBy2.count()
```
Transformations allow us to build up our logical transformation plan.
To trigger the computation, we run an *action*.
There are two types of transformations:
* those that specify *narrow dependencies*;
* those that specify *wide dependencies*;

Three kinds of actions:
* Actions to view data in the console;
* Actions to collect data to native objects in the respective language;
* Actions to write to output data sources;



## Running Spark
* `./bin/spark-shell` - to access the Scala console;
* `./bin/pyspark` - to access the Python console;
* `./bin/spark-submit` - to submit a precompiled applicaiton to Spark;

