The Nautilus DevOps team aims to containerize various applications following a recent meeting with the application development team. They intend to conduct testing with the following steps:


Install docker-ce and docker compose packages on App Server 2.


Initiate the docker service.


Approach:
1. ssh into app server 2 and switch to root
   ```
   ssh steve@stapp02
   sudo su
   ```
1. update the server repos
   ```
   yum update -y
   ```
2. Install the docker repo, if missing
   ```
   sudo yum install -y yum-utils
   sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
3. Install docker-ce
   ```
   yum install docker-ce
   ```
   
