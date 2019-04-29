git add .
git commit -m ""
git remote add origin remote repository URL
git remote -v
git push -u origin master


==================== Jenkins

docker run ^
  --rm ^
  -u root ^
  -p 8080:8080 ^
  -v jenkins-data:/var/jenkins_home ^
  -v /var/run/docker.sock:/var/run/docker.sock ^
  -v "%HOMEPATH%":/home ^
  --name jenkins-server ^
  jenkinsci/blueocean


docker run ^
  --rm ^
  -u root ^
  -p 8080:8080 ^
  -v jenkins-data:/var/jenkins_home ^
  -v /var/run/docker.sock:/var/run/docker.sock ^
  -v C:/Users/Test/Downloads:/home ^
  --name jenkins-server ^
  jenkinsci/blueocean

docker inspect name --> to see ports and ips
// If you’re using Docker Toolbox then any port you publish with docker run -p will be published on the Toolbox VM’s private IP address. docker-machine ip will tell you. It is frequently 192.168.99.100. 

localhost:8080
http://192.168.99.100:9091/

--- bash
docker exec -it jenkins-server bash


=========== Add Jenkinsfile to repo 




