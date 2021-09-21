# Recap On Docker (Containerization)[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)
## *Learning Docker Commands*


### Docker Useful Commands:

 1. Build from docker-compose file **(First Navigate to docker files directory)**:
 ```bash
docker-compose build
 ```
 2. Run Containers from docker-compose file:
```bash
docker-compose up
```
 3. Run Containers Detached from terminal (from docker-compose file):
```bash
docker-compose up -d
```
 4. Enter A Docker container and interact with it:
```bash
docker exec -it <container-name> /bin/bash
```
5. View running Containers:
```bash
docker ps -a
```
6. Pretty Printed (Formatted Output of running containers):
```bash
docker ps --filter status=exited --format "table {{.Names}}"
```
Example output:
```bash
NAMES
user2-10.9.0.2
ansible-base
user4-10.9.0.4
```
7. View Only names without table name:
```bash
docker ps --filter status=exited --format "{{.Names}}"
```
Example output:
```bash
user2-10.9.0.2
ansible-base
user4-10.9.0.4
```
8. Remove All Docker Via command Mentioned in **step 7** above:
```bash
docker rm $(docker ps --filter status=exited --format "{{.Names}}")
```
9. First You want to see all available docker images:
```bash
docker images
```
Example output:
```bash
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
mcnaughton/centos-base        latest    e76f0cd647f5   6 months ago   1.25GB
handsonsecurity/seed-ubuntu   large     cecb04fbf1dd   9 months ago   264MB
ansible/centos7-ansible       latest    688353a31fde   4 years ago    447MB
```

10. Format Results and only show Image ID:
```bash
docker images --format "{{.ID}}"
```
Example output:
```bash
e76f0cd647f5
cecb04fbf1dd
688353a31fde
```
11. Now Remove all Docker Images for make more space on disk:
```bash
docker rmi $(docker images --format "{{.ID}}"
```
Example output:
```bash
e76f0cd647f5
cecb04fbf1dd
688353a31fde
```