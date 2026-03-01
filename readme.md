<!-- FROM -> refer base OS
RUN -> configure the image, install, create user, folder, etc.
CMD -> command to start the container
ENTRYPOINT ->  command to start the container,but can't be overriden. used with CMD, CMD can supply default args. Users always can override default args
LABEL -> adds metadata to the image. used to filter
EXPOSE -> info about ports opened by container
ENV -> environment variables, containers can use
ARG -> build time variables. can be before FROM instruction to supply version to base OS. build variables can't be accessed inside container
COPY/ADD -> copies the files from local to image. ADD can download file from internet. ADD can directly untar the file into the image
USER -> default user to run the container
WORKDIR -> working directory for the container/image
ONBUILD -> force the users to follow ONBUILD instructions while using some image
image and container
image = bare min OS + System pacakges + Application Runtime + App code + dependencies
if You run image we get container, container is the running instance is image

docker ps -> all running docker containers
docker ps -a -> all containers
docker images -> images available in the server
docker pull <image-name>:<tag> -> pulls the image from docker hub
docker create imageID -> creates container from image
docker start containerID -> starts the container

docker run = pull + create + start
docker run -d 

growpart /dev/nvme0n1 4
lvextend -L +30G /dev/mapper/RootVG-varVol
xfs_growfs /var
/var/lib/docker -> docker home repo

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user

docker run -d -p <host-port>:<container-port> nginx

docker run -d -p 80:80 nginx

http://98.92.17.244

docker exec -it container-id bash
docker inspect image/containerID

Dockerfile -> Instructions to build custom images

Dockerfile

FROM
=====
refers to base OS of the image. your Dockerfile first instruction should be FROM

docker build -t <image-name>:<version> . -> . refers to current directory, it means Dockerfile is in current directory

docker push <URL>/<Username>/<image-name>:<version>


from 

docker.io/joindevops/from:version
ramesh/from

docker login

docker tag image-name:version username/image-name:version
docker push username/image-name:version

if you are pulling the image, first it checks whether it is available in local or not. if not available it pulls from central repo

docker rm -f `docker ps -a -q`

RUN
===
RUN instruction is used to configure the image. like installing packages, configurations, creating user, etc.

docker build --no-cache --progress=plain -t run:v1 .

CMD
====
referring the base image
configuring using RUN instruction

CMD ["nginx", "-g", "daemon off;"]

systemctl start nginx

CMD ["systemctl", "start", "nginx"] -> this will not work inside container, because does not have capabilities to contact kernal

instruction inside CMD should run the container for infinite time. command we are giving inside CMD should run in foreground, then we should take it into background

FROM almalinux:9

building the image
running the image

CMD -> instruction used to start the container

RUN -> executes at the time of image building
CMD -> executes at the time of container starting

image can have multiple run instructions
CMD should be only one, if we give multiple CMD last one is considered

LABEL
====
adds the metadata to the image, used for filtering

EXPOSE
======
it will not any functionality to the image/container, it adds the information about ports used by container

EXPOSE <port-number> -> it will not open the port, just for information

docker.joindevops.com/joindevops/from

session 53
=================
Notes
#!/bin/bash
growpart /dev/nvme0n1 4
lvextend -L +30G /dev/mapper/RootVG-varVol
xfs_growfs /var
dnf -y install dnf-plugins-core
dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
systemctl start docker
systemctl enable docker
usermod -aG docker ec2-user

docker exec -it containerid bash

FROM -> refer the base OS/image
RUN -> configure the image, like installing packages, users, etc.
CMD -> command to start the container
LABEL -> add the tags, key value pairs. basically metadata
EXPOSE -> ports information
COPY -> copy files from workspace to image

docker build -t URL/username/image-name:version .
docker build -t joindevops/from:v1 .

docker tag image-name:version username/image-name:version
docker push

ENV KEY=VALUE

ADD
===
ADD is also like COPY to copy the content inside the image. But ADD has 2 extra capabilities

1. It can directly fetch the content from internet
2. It can directly untar the file inside container/image

CMD ENTRYPOINT
==========
1. CMD instruction can be overriden.
2. ENTRYPOINT can't be overriden, if we try it will go and append that leads to failure
3. CMD can be used to supply the default args to ENTRYPOINT. You can always override the default args at run time

ARG
===
ARG can be the first instruction in an exceptional case i.e to supply the version to the base image.. after FROM instruction we can't access ARG variable

ARG vs ENV
==========
1. ENV is used to supply the key value pairs for the container/runtime
2. ARG is used to supply the values to variables at build time.
3. ARG can't be accessible inside container. -->