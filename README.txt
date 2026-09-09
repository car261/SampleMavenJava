DOCKER FILE

FROM tomcat:9.0
COPY target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 7089
CMD ["catalina.sh","run"]

FROM eclipse-temurin:17-jdk 
COPY target/*.jar app.jar 
EXPOSE 6379 
CMD ["java", "-jar", "app.jar"]

java -jar target/app.jar

mvn test -Dsurefire.rerunFailingTestsCount=1
-----------------------------------------
docker ps -a
docker image ls
docker build -t lmsimage .
docker run -d -p 7089:8080 --name lmcontainer lmsimage
docker ps
docker rm -f lmcontainer
docker login
docker tag lmsimage thedanny69/lmsimage:latest
docker push thedanny69/lmsimage:latest

docker rmi old_api
docker exec -it web_app /bin/bash
docker logs web_app
docker run -d --restart=always web_app
-----------------------------------------
surya@Danny MINGW64 /d/LMSWEBP (main)
$ docker run -it ubuntu bash

root@b78ac9785852:/# ls
bin   dev  home  lib64  mnt  proc  run   srv  tmp  var
boot  etc  lib   media  opt  root  sbin  sys  usr
root@b78ac9785852:/# pwd
/
root@b78ac9785852:/# exit
exit
------------------------------------------------
surya@Danny MINGW64 /d/LMSWEBP (main)
$ docker ps -a
CONTAINER ID   IMAGE      COMMAND                  CREATED             STATUS                      PORTS                                         NAMES
b78ac9785852   ubuntu     "bash"                   51 seconds ago      Exited (0) 37 seconds ago                                                 clever_pare

surya@Danny MINGW64 /d/LMSWEBP (main)$ 
docker stop b78ac9785852
b78ac9785852
----------------------------------------------------


GIT

git status
git init
git config --global user.name "Surya Dhanush"
git config --global user.email "sssd749445@gmail.com"
git add .
git commit -m "First commit"
git remote set-url origin https://github.com/Suryadhanush609/LMSWEBP.git
git push -u origin main
git branch -M main
-------------------------------------------------------
org.apache.maven simple
gid: com.example
artifact_id=name
