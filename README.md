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

## Install composer
1. open terminal and download composer composer.phar
```
$ curl -s https://getcomposer.org/installer | php
```
2. move composer.phar to bin
```
$ sudo mv composer.phar /usr/local/bin/
```
3.  go to /usr/bin/ folder to create an alias:
```
$ vim ~/.bash_profile
```
then add following script by enter 'I' as insert mode
```
alias composer="php /usr/local/bin/composer.phar"
```
press ESC, and :wq to save and quit
4. quit terminal and reopen a new terminal, type
```
$ composer
```
5. Install PHPunit by creating composer.json file under the project folder
```
{
    "require-dev": {
        "phpunit/phpunit": "3.7.*"
    }
}
```
then run command under the project folder
```
composer update
```

## Setup php development enviroment with XAMPP
1. Install XAMPP

## Configure mutiple virtual hosts in XAMPP

1. Enable VirtualHosts. 
Open file 
```
/Applications/XAMPP/xamppfiles/etc/httpd.conf
```
locate the # Virtual hosts section, and uncommend the following line as below 
```
# Virtual hosts
# Include /Applications/XAMPP/etc/extra/httpd-vhosts.conf
```
then save the changes.

2. Create custom virtualhosts configuration. 
Open file 
```
/Applications/XAMPP/xamppfiles/etc/extra/httpd-vhosts.conf
```
at the bottom line, add default virtual host for localhost
```
<VirtualHost *:{port number}>
    ServerName localhost
    DocumentRoot "/Applications/XAMPP/xamppfiles/htdocs"
    <Directory "/Applications/XAMPP/xamppfiles/htdocs">
        Options Indexes FollowSymLinks Includes execCGI
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
Then add custom virtual host
```
<VirtualHost *:{port number}>
    ServerName mysite.local
    DocumentRoot "/Users/{yourusername}/{site path}"
    <Directory "/Users/{yourusername}/{site path}">
        Options Indexes FollowSymLinks Includes ExecCGI
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog "logs/mysite.local-error_log"
</VirtualHost>
```
3. Update hosts file. 
Go to terminal, enter 
```
$ sudo nano /etc/hosts
```
then add following configuration at the bottom of line
```
127.0.0.1 mysite.local
```
Press Control+x to save and quit from the file.

4. Restart Apache.

5. open phpmyadmin http://localhost:8091/phpmyadmin/index.php

6. mysql db database user/password - root/null by default


