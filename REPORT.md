# My Docker Assignment Report

Name: Kinana Alasheq_

Repository URL: ____________________

Use short sentences. Add the answers requested in the assignment PDF.
Keep passwords, tokens, and private keys out of this report.


## Mission 1 - First Container

Commands used:
docker pull nginx:alpine
docker run -d --name web-server -p 8080:80 nginx:alpine
docker ps
docker logs web-server
docker inspect web-server
docker exec -it web-server sh
pwd
ls
cat /etc/os-release

ًWhat happened:
The Nginx container run successfully, and the welcome page opened in my browser.

What I learned:
how to run, inspect, and access a Docker container

Problem I faced:
No problems

How I fixed it:
No fixes
____________________

## Mission 2 - Build Your Own Image

Commands used:
docker build -t devops-node-app:v1 .
docker images
docker run -d --name node-app -p 8081:3000 devops-node-app:v1
docker exec -it node-app sh
pwd
ls
cat message.txt
docker build -t devops-node-app:v2 .
docker rm -f node-app
docker run -d --name node-app -p 8081:3000 devops-node-app:v2
docker ps

What happened:
1-build a Docker image from Node.js application then run successfully in container
2-changing message.txt on my host machine but the running container still displayed the old message.
3-After rebuilding the image as v2 and creating a new container, the updated message appear

What I learned:
1-create a Dockerfile
2-build an image
3-run a container
4-changes to host files don't automatically update an existing Docker image or container. I must rebuild the image to include
changes.

Problem I faced:
Port 8080 is allocated to Nginx container in task1. that does a conflict

How I fixed it:
1-used port 8081 instead of 8080
2- remove old container then start the new application with new port

____________________

## Mission 3 - Broken Port

Commands used:
docker ps -a
docker logs broken-app
docker rm -f broken-app
docker run -d --name broken-app -p 8080:3000 devops-node-app:v1
docker ps

What happened:
The application is running, but the website isn't reachable

What I learned:
troubleshoot Docker port mapping problems

Problem I faced:
The container port was incorrectly set to 5000 instead of 3000

How I fixed it:
changed the port mapping to 8080:3000
____________________

## Mission 4 - Environment Variables

Commands used:
docker run -d --name env-app -p 8082:3000 -e APP_MESSAGE="Hello from the Docker assignment" devops-node-app:v1
docker exec -it env-app sh
printenv APP_MESSAGE
docker rm -f env-app
docker run -d --name env-app -p 8082:3000 -e APP_MESSAGE="Another message without rebuilding" devops-node-app:v1

What happened:
The application displayed different messages using environment variables without rebuilding the image

What I learned:
Environment variables can change application settings when starting a container

Problem I faced:
no

How I fixed it:
no
___________________

## Mission 5 - Docker Hub

Commands used:
docker login
docker tag devops-node-app:v2 kinanaalasheq/devops-node-app:v2
docker push kinanaalasheq/devops-node-app:v2

What happened:
uploaded my Docker image to my Docker Hub repository successfully

What I learned:
tag and push Docker images to Docker Hub

Problem I faced:
The first push failed because the username contained uppercase letters

How I fixed it:
used the lowercase username and pushed the image successfully
___________________

## Mission 6 - Remote Deployment

Commands used:
sudo docker login
sudo docker pull kinanaalasheq/devops-node-app:v2
sudo docker run -d --name remote-node-app -p 8080:3000 kinanaalasheq/devops-node-app:v2
sudo docker ps
curl http://localhost:8080

What happened:
pulled my private Docker image from Docker Hub and successfully run it on an Ubuntu VM

What I learned:
pull and run a private Docker image on a remote Linux machine

Problem I faced:
Docker was not installed on the Ubuntu VM initially, and DNS resolution was not working

How I fixed it:
I installed Docker, fixed DNS settings, logged in to Docker Hub, and successfully ran the container
____________________

## Mission 7 - Volumes

Commands used:
docker run -d --name mongo-lab mongo:7
docker exec mongo-lab mongosh --quiet --eval 'db.getSiblingDB("devops").messages.insertOne({text:"keep-me"})'
docker rm -fv mongo-lab
docker run -d --name mongo-lab mongo:7
docker exec mongo-lab mongosh --quiet --eval 'db.getSiblingDB("devops").messages.find().toArray()'
docker rm -f mongo-lab
docker volume create mongo-data
docker run -d --name mongo-lab -v mongo-data:/data/db mongo:7
docker rm -f mongo-lab
docker run -d --name mongo-lab -v mongo-data:/data/db mongo:7
docker exec mongo-lab mongosh --quiet --eval 'db.getSiblingDB("devops").messages.find().toArray()'

What happened:
Without a volume, the record disappeared after recreating the container. With the named volume, the record survived.

What I learned:
Docker volume stores database data separately from the container

Problem I faced:
The data was lost when I removed the first MongoDB container

How I fixed it:
created and reused the named volume ---> mongo-data
______________________

## Mission 8 - Docker Networking

Commands used:
docker compose up --build -d
docker compose logs app
docker network inspect 08-networking-challenge_default
docker compose up -d --force-recreate app
docker compose logs --tail=15 app

What happened:
The app initially could not connect to PostgreSQL. After fixing the network configuration
the app connected successfully

What I learned:
Containers should connect using the service name instead of localhost

Problem I faced:
The app could not reach PostgreSQL, and port 8081 was already in use

How I fixed it:
I changed DB_HOST from localhost to postgres, stopped the old node-app container
and recreated the app container to connect it to the Compose network

____________________

## Mission 9 - Docker Compose

Commands used:

____________________

What happened:

____________________

What I learned:

____________________

Problem I faced:

____________________

How I fixed it:

____________________

## Bonus Mission

Commands used:

____________________

What happened:

____________________

What I learned:

____________________

Problem I faced:

____________________

How I fixed it:

____________________
