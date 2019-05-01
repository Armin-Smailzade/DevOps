=============== java 11
sudo apt install -y openjdk-11-jdk

=============== maven
sudo apt install -y maven

mvn archetype:generate -DgroupId=com.c1b.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

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

=============== Git
git add .
git commit -m ""
git remote add origin remote repository URL
git remote -v
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


=========== Add Jenkinsfile to repo 




