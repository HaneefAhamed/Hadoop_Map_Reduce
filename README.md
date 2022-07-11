# Introduction to Hadoop 

In this project, we setup Hadoop in docker, do basic pragramming in Hadoop such as n-gram and develop MapReduce programs to analyze a real anonymous logs to 
answer several questions based on the log. 

## Setting up Hadoop in docker

First, we need to build  container  from  Docker  (https://www.docker.com/)  images. Docker is an emerging virtualization  tool  which is  similar to  the previous  tool,  Sandbox.  It  provides  several  good features  to  the  system  developers.  You  can  treat  it  as  the  fusion  of  version  control  system (VCS)  and  Programming  Language  (like  JAVA)  for  virtual  machines.  You  can  start  with building a small Ubuntu (one of the Linux distributions) image first. Check get started with Docker  for  Windows  (https://docs.docker.com/desktop/windows/),  how  to  build  a  Docker image (https://docs.docker.com/get-started/) for details. Second, based on Ubuntu Docker image, you can build the Hadoop Docker image with the help of the bash files we uploaded. You can start with a basic Hadoop which runs the tasks locally.
