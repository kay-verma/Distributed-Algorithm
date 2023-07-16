# ZNode Election and Re-election using ZooKeeper

This repository contains an example implementation of ZNode election and re-election using Apache ZooKeeper. It demonstrates how to use ZooKeeper's coordination features to elect a leader among a group of nodes and handle re-election scenarios.

## Background

ZooKeeper is a distributed coordination service that provides primitives for building distributed applications. One of its key features is the ability to elect a leader among a group of nodes. This leader election mechanism can be useful in scenarios where only one node needs to perform certain tasks or take critical decisions.

This example demonstrates how to use ZooKeeper's ZNode's to perform leader election and handle re-election scenarios. It showcases the process of electing a leader initially and handling scenarios where the leader node goes down or disconnects, triggering a re-election.

## Prerequisites

Apache ZooKeeper installed and running on your system. You can download ZooKeeper from the official Apache ZooKeeper website (https://zookeeper.apache.org).
Apache Maven installed on your system. You can download Maven from the official Apache Maven website (https://maven.apache.org).

## Installation

Clone this repository to your local machine:
shell
Copy code
git clone https://github.com/example-user/znode-election.git
Navigate to the project directory:
```
cd znode-election
```
## Usage

Start four ZooKeeper nodes in separate terminals, each running on a different port:

Terminal :
```
zkServer.sh start-foreground zoo1.cfg 
```

Ensure that the zoo1.cfg, zoo2.cfg, zoo3.cfg, and zoo4.cfg files are properly configured with unique port numbers.
Build and package the project using Maven:
```
mvn clean package
```
Run the example code with four ZooKeeper nodes:
```
java -jar target/znode-election.jar localhost:2181,localhost:2182,localhost:2183,localhost:2184
```
Ensure that you provide the appropriate ZooKeeper ensemble connection string, consisting of the four ZooKeeper nodes' host and port information.

Observe the console output to see the leader election process. You will see messages indicating which node has been elected as the leader and any re-elections that occur.
Testing and Failure Handling
![Image Description](Screenshot2023-07-17at5.07.03AM.png)


## To test the failure handling and re-election process, follow these steps:

Once the cluster is up and running, identify the leader node from the console output.
Inject a failure into the leader node by stopping it or terminating its process.
Observe the console output to see how the remaining nodes handle the failure and initiate a new leader election process.
#### Note the new leader elected by the cluster and observe any re-elections that occur due to the failure. Repeat the process by injecting failures into different nodes to simulate various failure scenarios and validate the re-election process.
