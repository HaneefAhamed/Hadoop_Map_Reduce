# Introduction to Hadoop 

In this project, we setup Hadoop in docker, do basic pragramming in Hadoop such as n-gram and develop MapReduce programs to analyze a real anonymous logs to 
answer several questions based on the log. 

## Setting up Hadoop in docker

First, we need to build  container  from  Docker  (https://www.docker.com/)  images. Docker is an emerging virtualization  tool  which is  similar to  the previous  tool,  Sandbox.  It  provides  several  good features  to  the  system  developers.  You  can  treat  it  as  the  fusion  of  version  control  system (VCS)  and  Programming  Language  (like  JAVA)  for  virtual  machines.  You  can  start  with building a small Ubuntu (one of the Linux distributions) image first. Check get started with Docker  for  Windows  (https://docs.docker.com/desktop/windows/),  how  to  build  a  Docker image (https://docs.docker.com/get-started/) for details. Second, based on Ubuntu Docker image, you can build the Hadoop Docker image with the help of the bash files we uploaded. You can start with a basic Hadoop which runs the tasks locally.

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
 
# RUN is a basic command in Dockerfile to run system call as in the terminal for buildi
ng the Docker image 
# You can install packages and download Hadoop using RUN command  
 
# ADD file, hdfs-site.xml in the current directory, to the directory, $HADOOP_PREFIX/e
tc/hadoop/hdfs-site.xml, in the image 
ADD hdfs-site.xml $HADOOP_PREFIX/etc/hadoop/hdfs-site.xml
 # EXPOSE informs Docker that the container listens on the specified network ports at r
untime 
EXPOSE 50010 
 
# CMD setups a call which is run when the docker image starts, which can be called on
ce in the Dockerfile 
CMD ["/etc/bootstrap.sh", "-d"]
