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

## Install mysql docker container
Press command + space to open up the quick search window, Then enter 'terminal' to open the Terminal'
1. $ docker search mysql (show all available mysql)
2. $ docker pull mysql (download mysql docker image)
3. $ docker images (verify downloaded images)
3. $ docker run --name mysql -e MYSQL_ROOT_PASSWORD=root123 -p 3306:3306 -d mysql (create and run mysql container at the first time)
4. $ docker stop mysql (stop mysql container)
5. $ docker start mysql (start mysql container)
6. $ docker rm mysql (delete existing mysql container)

## Install phpmyadmin docker container
Press command + space to open up the quick search window, Then enter 'terminal' to open the Terminal'
1. $ docker search phpmyadmin (show all available mysql)
2. $ docker pull phpmyadmin/phpmyadmin (download phpmyadmin docker image)
3. $ docker images (verify downloaded images)
3. $ docker run --name phpmyadmin --link mysql:db -p 8089:80 -d phpmyadmin/phpmyadmin
4. $ docker stop phpmyadmin (stop phpmyadmin container)
5. $ docker start phpmyadmin (start phpmyadmin container)
6. $ docker rm phpmyadmin (delete existing phpmyadmin container)
7. go web browser: http://localhost:8089
8. username:password root:root123 by default

## Enable PHP & Apache on MacOS
1. Press command + space to open up the quick search window, Then enter 'terminal' to open the Terminal'
2. $ sudo su -
3. $ apachectl start (enable apache)
4. Open web browser: http://localhost/ to test it
5. $ cd /etc/apache2
6. $ cp httpd.conf httpd.conf.sierra
7. $ vi httpd.conf, then uncomment line of LoadModule php5_module libexec/apache2/libphp5.so (enable php in apache)
8. $ apachectl restart (restart apache)
9. Create the phpinfo.php file in your DocumentRoot (/Library/WebServer/Documents/)





## Install php docker container

