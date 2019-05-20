============================== Git
git add .
git commit -m ""
git remote add origin remote repository URL
git remote -v
git push -u origin master


====> create a new repository on the command line
echo "# springbootkbe" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/Armin-Smailzade/springbootkbe.git
git push -u origin master

====> push an existing repository from the command line
git remote add origin https://github.com/Armin-Smailzade/springbootkbe.git
git push -u origin master


====> create branch 
git branch <feature_branch>
git checkout <feature_branch>
git add .
git commit -m "adding a change from the feature branch"
git push origin <feature_branch>

============================== java 11
sudo apt install -y openjdk-11-jdk

============================== maven
sudo apt install -y maven

mvn archetype:generate -DgroupId=com.c1b.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

============================== gradle
wget https://services.gradle.org/distributions/gradle-5.4.1-bin.zip -P /tmp
sudo unzip -d /opt/gradle /tmp/gradle-*.zip
ls /opt/gradle/gradle-5.4.1
sudo nano /etc/profile.d/gradle.sh
  export GRADLE_HOME=/opt/gradle/gradle-5.4.1
  export PATH=${GRADLE_HOME}/bin:${PATH}
sudo chmod +x /etc/profile.d/gradle.sh
source /etc/profile.d/gradle.sh

sudo chown -R cloud_user:cloud_user /home/cloud_user/my-project/

sudo chown -R armin.emsaeilzadeh:armin.emsaeilzadeh /home/armin.emsaeilzadeh/okta-spring-boot-microservice-kubernetes/

============================== Docker
https://gist.github.com/LeCoupa/f975e330551508ffd598a0d4bc4bed38

sudo apt install -y docker.io
service docker start
docker info

systemctl unmask docker.service
systemctl unmask docker.socket
systemctl start docker.service

sudo su
passwd ubuntu
27646@Leo

==== Docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
====

sudo touch ./Dockerfile
sudo vi ./Dockerfile
	copy content to dockerfile
	Esc key
	:wq -> enter

docker build -f Dockerfile[filePath] -t demo/oracle-java:latest[name:tag] .[context]

-p 8081:8080


docker image ls
docker run demo/oracle-java
docker ps
docker stop demo/oracle-java
docker restart demo/oracle-java
docker rm demo/oracle-java

gcr.io/spring-boot-gke-239421/kayak-app:1.0

docker build -t kayak-app:1.0 .
docker tag kayak-app:1.0 gcr.io/spring-boot-gke-239421/kayak-app:1.0;
docker push gcr.io/spring-boot-gke-239421/kayak-app:1.0

=============== Docker Logs

docker-compose logs rabbit
docker-compose logs --tail 5 rabbit

docker-compose logs -t   

docker logs -t --since 2018-03-03T16:52:45.000996884Z --until 2018-03-03T16:52:45.001996884Z docker_rabbit_1

docker logs -t --tail 10 docker_rabbit_1 | grep info

docker logs -t --tail 10 docker_rabbit_1 | grep info >> my_log_file.txt


=============== Docker clean

docker system prune

docker system prune --volumes

docker container ls -a --filter status=exited --filter status=created 

docker container prune
docker container prune --filter "until=12h"

docker container stop $(docker container ls -aq)
docker container rm $(docker container ls -aq)

docker image prune
docker image prune -a
docker image prune -a --filter "until=12h"

docker volume prune
docker network prune

docker network prune -a --filter "until=12h"

============================== NginX
https://www.digitalocean.com/community/tutorials/how-to-run-nginx-in-a-docker-container-on-ubuntu-14-04

mkdir -p ~/docker-nginx/html
cd ~/docker-nginx/html
vim index.html

<html>
  <head>
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet" integrity="sha256-MfvZlkHCEqatNoGiOXveE8FIwMzZg4W85qfrfIFBfYc= sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">
    <title>Docker nginx Tutorial</title>
  </head>
  <body>
    <div class="container">
      <h1>Hello Digital Ocean</h1>
      <p>This nginx page is brought to you by Docker and Digital Ocean</p>
    </div>
  </body>
</html>

sudo docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx


=============== Redis - Docker

docker run --name my-redis -p 6379:6379 -d redis
docker run -it --link my-redis:redis redis redis-cli -h redis -p 6379

============================== Redis
https://www.concretepage.com/spring-boot/spring-boot-redis
https://www.journaldev.com/18141/spring-boot-redis-cache
https://logz.io/blog/kafka-vs-redis/

https://piotrminkowski.wordpress.com/2019/03/18/redis-in-microservices-architecture/
1- messeging
2- config server
3- persistent

Redis Cluster
https://redis.io/topics/partitioning


https://dzone.com/articles/3-ways-to-use-redis-hash-in-java
- jedis.hget(name, keyArray); //only takes byte arrays
- RedisTemplate<String,Object> //provide serialize deserialize impl
- Redisson
- @Cashable


============= Commands
https://gist.github.com/LeCoupa/1596b8f359ad8812c7271b5322c30946


redis-cli
redis-cli INFO | grep conected
CONFIG GET *
CONFIG SET timeout 900

redis-cli INFO | grep ^db \\separated namespaces called "databases"
select 1
FLUSHDB
FLUSHALL

INFO | grep role

SLAVEOF <IP> <port> \\quickly need to set up replication. run on slave machine

CLIENT LIST
CLIENT KILL <IP>:<port>

MONITOR

KEYS test*

============================== Kafka
https://docs.confluent.io/current/quickstart/ce-docker-quickstart.html
https://www.confluent.io/blog/apache-kafka-spring-boot-application
https://github.com/igorkosandyak/spring-boot-kafka
https://www.baeldung.com/spring-kafka
https://github.com/eugenp/tutorials/tree/master/spring-kafka

============================== Cassandra


============================== MySQL




============================== Jenkins

docker run \
  --rm \
  -u root \
  -p 8080:8080 \
  -v jenkins-data:/var/jenkins_home \ 
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME":/home \ 
  --name jenkins-server
  jenkinsci/blueocean

docker run --rm -u root -p 8080:8080 -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v "$HOME":/home --name jenkins-server jenkinsci/blueocean

docker run ^
  --rm ^
  -u root ^
  -p 8080:8080 ^
  -v jenkins-data:/var/jenkins_home ^
  -v /var/run/docker.sock:/var/run/docker.sock ^
  -v "%HOMEPATH%":/home ^
  --name jenkins-server ^
  jenkinsci/blueocean


docker inspect name --> to see ports and ips
// If you’re using Docker Toolbox then any port you publish with docker run -p will be published on the Toolbox VM’s private IP address. docker-machine ip will tell you. It is frequently 192.168.99.100. 

localhost:8080
http://192.168.99.100:9091/

--- bash
docker exec -it jenkins-server bash


============================== Kubectl
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl

============================== Config Server 

spring boot
https://medium.com/design-and-tech-co/creating-a-configuration-microservice-using-spring-cloud-config-800d08fa596a




============================== Bash
https://gist.github.com/LeCoupa/122b12050f5fb267e75f

============================== AWS
apt-get install awscli

curl -s http://169.254.169.254/latest/meta-data/


============================== Linux

// header information, silence body 
curl -I -s https://opensource.com 

cat test.json | python -m json.tool

ls -l 

// follow
tail -f /var/log/httpd/access_log 
// n=100
tail -n 100 /var/log/httpd/access_log 

cat tomcat.log | grep org.apache.catalina.startup.Catalina.start

//shows process status
ps -ef | grep tomcat 

env

//sorted process information
top

// network ports in use and their incoming connections
netstat 

// shows the interfaces and IP addresses of your application's host
ip address

// lists the open files associated with your application
//any interaction with the system is treated like a file
lsof -i tcp:80
lsof -p 18311

//display free disk space
df -h
df -i
du -sh /var/log/*    //total Size , Human readable

// user identity
id 

//permission. -x adds executing to the permissions
chmod -x test.sh
ls -l 

//query internet name servers
nslookup mydatabase
dig mydatabase


//blocks or allows traffic on a Linux host
iptables -S

//provides least-privilege access to processes running on the host
sestatus // see if it is enabled

history


============================================= NoSQL
https://www.kdnuggets.com/2018/08/dynamodb-vs-cassandra.html
https://aws.amazon.com/blogs/big-data/best-practices-for-running-apache-cassandra-on-amazon-ec2/



============================================= Links
https://www.baeldung.com/spring-cloud-bootstrapping

https://www.baeldung.com/spring-cloud-tutorial


https://www.baeldung.com/rest-api-spring-oauth2-angular


https://github.com/eugenp/tutorials/tree/master/core-java-8

https://sssit.org/core-java-syllabus


https://www.journaldev.com/2389/java-8-features-with-examples


https://stackify.com/guide-docker-java/


==========================
https://medium.com/@maxy_ermayank/pipeline-as-a-code-using-jenkins-2-aa872c6ecdce


https://www.weave.works/technologies/kubernetes-on-aws/

https://ramhiser.com/post/2018-05-20-setting-up-a-kubernetes-cluster-on-aws-in-5-minutes/

https://www.guru99.com/nosql-tutorial.html

https://medium.com/@michaeljpr/five-minute-guide-getting-started-with-cassandra-on-docker-4ef69c710d84

https://github.com/wsargent/docker-cheat-sheet

file:///C:/Users/azadeh/Downloads/NCC_Group_Understanding_Hardening_Linux_Containers-1%201.pdf
https://dzone.com/articles/microservices-in-practice-1

https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

https://docs.aws.amazon.com/aws-technical-content/latest/microservices-on-aws/service-discovery.html

https://12factor.net/

https://medium.com/@odedia/spring-session-redis-part-i-overview-a5f6c7446c8b

https://istio.io/docs/concepts/what-is-istio/

https://developer.okta.com/blog/2019/04/01/spring-boot-microservices-with-kubernetes

https://supergiant.io/blog/kubernetes-networking-explained-introduction/




