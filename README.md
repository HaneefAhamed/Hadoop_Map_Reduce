# Introduction to Hadoop 

In this project, we setup Hadoop in docker, do basic programming in Hadoop such as n-gram and develop MapReduce programs to analyze a real anonymous logs to 
answer several questions based on the log. 

## Setting up Hadoop in docker

First, we need to build  container  from  Docker  (https://www.docker.com/)  images. Docker is an emerging virtualization  tool  which is  similar to  the previous  tool,  Sandbox.  It  provides  several  good features  to  the  system  developers.  You  can  treat  it  as  the  fusion  of  version  control  system (VCS)  and  Programming  Language  (like  JAVA)  for  virtual  machines.  You  can  start  with building a small Ubuntu (one of the Linux distributions) image first. Check get started with Docker  for  Windows  (https://docs.docker.com/desktop/windows/),  how  to  build  a  Docker image (https://docs.docker.com/get-started/) for details. Second, based on Ubuntu Docker image, you can build the Hadoop Docker image with the help of the bash files we uploaded. You can start with a basic Hadoop which runs the tasks locally.

```
#Set the basic image for this Docker image 
FROM ubuntu:16.04 
#Set the id of the maintainer of the image which can be assigned on the Docker Hub 
MAINTAINER your-id 
# Assign the user to run the system calls 
USER root 
 
# ENV is a basic command in Dockerfile to set the Environment variables 
ENV JAVA_HOME /usr/java/default 
ENV PATH $PATH:$JAVA_HOME/bin 
ENV java_path /usr/lib/jvm/java-8-openjdk-amd64 
 
# RUN is a basic command in Dockerfile to run system call as in the terminal for building the Docker image 
# You can install packages and download Hadoop using RUN command  
 
# ADD file, hdfs-site.xml in the current directory, to the directory, $HADOOP_PREFIX/etc/hadoop/hdfs-site.xml, in the image 
ADD hdfs-site.xml $HADOOP_PREFIX/etc/hadoop/hdfs-site.xml

# EXPOSE informs Docker that the container listens on the specified network ports at runtime 
EXPOSE 50010 
 
# CMD setups a call which is run when the docker image starts, which can be called once in the Dockerfile 
CMD ["/etc/bootstrap.sh", "-d"]
```

Check  Dockerfile  reference  (https://docs.docker.com/engine/reference/builder/)  for  basic docker commands, and Hadoop: Setting up a Single Node Cluster (https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/SingleCluster.html) for instruction on configurations. You can build the Docker image based on that Dockerfile. 

## Developing a Hadoop program

Develop a Hadoop program that produces the n-gram  frequencies  of  the  text  in  a  given  input  file.  n-gram  is  a  contiguous  sequence  of  n characters from a given sequence of text. 

An n-gram of size 1 is referred to as a "unigram"; size 2 is a "bigram" (or, less commonly, a "digram"); size 3 is a "trigram". For example, the 2-gram frequency in the text, “Helloworld” is as follows: 

He-1, el-1, ll-1, lo-1, ow-1, wo-1, or-1, rl-1, ld-1 

Your program should accept n as an input parameter and produce the n-gram frequencies in the text as an output file.

## Developing a Hadoop program to analyze real logs using MapReduce

Develop MapReduce programs to analyze a real anonymous logs to answer several questions based on the log. The log is in access_log. The log file is in Common Log Format

``` ruby
10.223.157.186 - - [15/Jul/2009:15:50:35 -0700] "GET /assets/js/lowpro.js HTTP/1.1" 
200 10469 
 
%h %l %u %t \"%r\" %>s %b 
```

```
Where: 
• %h is the IP address of the client 
• %l is identity of the client, or "-" if it's unavailable 
• %u is username of the client, or "-" if it's unavailable 
• %t is the time that the server finished processing the request. The format is [day/month/year:hour:minute:second zone] 
• %r is the request line from the client is given (in double quotes). It contains the method, path, query-string, and protocol or the request. 
• %>s is the status code that the server sends back to the client. You will see see mostly status codes 200 (OK - The request has succeeded), 304 (Not Modified) and 404 (Not Found). See more information on status codes in W3C.org 
• %b is the size of the object returned to the client, in bytes. It will be "-" in case of status code 304.
```

Questions: 

1. How many hits were made to the website item “/assets/img/home-logo.png”? 
2. How many hits were made from the IP: 10.153.239.5 
3. Which path in the website has been hit most? How many hits were made to the path? 
4. Which IP accesses the website most? How many accesses were made by it? 
