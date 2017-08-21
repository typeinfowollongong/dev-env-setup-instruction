# Local Development Enviroment Setup Instruction

## Install JDK on MAC
java8 available download from http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

## Install docker on MAC
available download from https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac
1. $ docker images (list all pulled images)
2. $ docker ps -a (list existing running container)
3. $ docker-machine ip default (list docker ip)
4. $ docker rmi $(docker images) -q


## Install Jenkins docker container
Jenkins docker image pull from https://hub.docker.com/r/jenkinsci/jenkins
Install instructions at https://wiki.jenkins-ci.org/display/JENKINS/Installing+Jenkins+with+Docker
Notes:
1. create Jenkins home folder $PWD/jenkins
2. $ docker run -it -p 48082:8080 -v $PWD/jenkins:/var/jenkins_home:z -t jenkinsci/jenkins:lts
3. $ docker start [container id]


## Install nexus docker container
image pull from https://hub.docker.com/r/sonatype/nexus/

1. open docker command line
2. $ docker pull sonatype/nexus (download nexus docker image)
3. $ docker run -d -p 8081:8081 --name nexus sonatype/nexus:oss (create and run nexus container at the first time)
4. $ docker stop nexus (stop nexus container)
5. $ docker start nexus (start nexus container)
6. $ docker rm nexus (delete existing nexus container)

default url: http://localhost:8081/nexus/ 
default user/password: admin/admin123

## Install mysql+phpadmin docker container
image pull from https://hub.docker.com/r/sonatype/nexus/

1. open docker command line
2. $ docker pull sonatype/nexus (download nexus docker image)
3. $ docker run -d -p 8081:8081 --name nexus sonatype/nexus:oss (create and run nexus container at the first time)
4. $ docker stop nexus (stop nexus container)
5. $ docker start nexus (start nexus container)
6. $ docker rm nexus (delete existing nexus container)

default url: http://localhost:8081/nexus/ 
default user/password: admin/admin123
