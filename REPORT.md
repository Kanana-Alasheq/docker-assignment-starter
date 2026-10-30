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

____________________

What happened:

____________________

What I learned:

____________________

Problem I faced:

____________________

How I fixed it:

____________________

## Mission 5 - Docker Hub

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

## Mission 6 - Remote Deployment

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

## Mission 7 - Volumes

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

## Mission 8 - Docker Networking

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
