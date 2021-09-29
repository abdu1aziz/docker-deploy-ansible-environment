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

12. Use the following commands to keep track of the docker containers running in the background.
```bash
docker stats
```
Example output:
```bash
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O         PIDS
65e46bca3755   ansible-base     1.17%     606.6MiB / 2GiB       29.62%    0B / 0B       1.51GB / 2.82GB   228
a71f83c42ac3   user4-10.9.0.4   0.00%     2.98MiB / 15.62GiB    0.02%     6.02kB / 0B   0B / 0B           1
b7bc232bd896   user2-10.9.0.2   0.00%     1.672MiB / 15.62GiB   0.01%     6.02kB / 0B   0B / 0B           1
60ea964f01d8   user3-10.9.0.3   0.00%     2.961MiB / 15.62GiB   0.02%     6.02kB / 0B   0B / 0B           1
``