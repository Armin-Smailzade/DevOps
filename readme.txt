=============== java 11
sudo apt install -y openjdk-11-jdk

=============== maven
sudo apt install -y maven

mvn archetype:generate -DgroupId=com.c1b.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

=============== gradle
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

=============== Docker
sudo apt install -y docker.io
service docker start
docker info

systemctl unmask docker.service
systemctl unmask docker.socket
systemctl start docker.service

sudo su
passwd ubuntu
27646@Leo


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

========
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


=============== Git
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


==================== Jenkins

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


=========== Kubectl
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl

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




