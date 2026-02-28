ARG
===
ARG can be the first instruction in an exceptional case i.e to supply the version to the base image.. after FROM instruction we can't access ARG variable

ARG vs ENV
==========
1. ENV is used to supply the key value pairs for the container/runtime
2. ARG is used to supply the values to variables at build time.
3. ARG can't be accessible inside container.

PRACTICE 
-----------------
3.233.234.102 | 172.31.70.87 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-70-87 ~/dockerfiles/ARG ]$ docker build -t arg:v1 --build-arg VERSION=8 --build-arg COURSE=AWS .
[+] Building 5.4s (6/6) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 289B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:8                                            0.3s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => [1/2] FROM docker.io/library/almalinux:8@sha256:6e0bf7e15bf9082c3e5b8f1811618ae2c56c7b9fc1e9f5e5ec6e  4.1s
 => => resolve docker.io/library/almalinux:8@sha256:6e0bf7e15bf9082c3e5b8f1811618ae2c56c7b9fc1e9f5e5ec6e  0.0s
 => => sha256:ae93eb8e046d556eab73821be1ee598d67cbdaf19013e6a1574362d11dc09bb8 71.90MB / 71.90MB          1.1s
 => => extracting sha256:ae93eb8e046d556eab73821be1ee598d67cbdaf19013e6a1574362d11dc09bb8                 2.9s
 => [2/2] RUN echo "Trainer: SIVAKUMAR, Course: AWS, Version: ${VERSION}"                                 0.6s
 => exporting to image                                                                                    0.3s
 => => exporting layers                                                                                   0.1s
 => => exporting manifest sha256:093886f36fbe86922ca553214e8aaeb45a8119c2bdf17ddaf4fec84c0564e1c4         0.0s
 => => exporting config sha256:3a1113e9bf1454eb3f3076fd740313e837da071d58f28e35aed3bf3c3c901d43           0.0s
 => => exporting attestation manifest sha256:5e488bcb7808123c91c1f219a2a348fe1cfb344e46b246ff2ac6382fe0c  0.0s
 => => exporting manifest list sha256:fc0dc788a53b2771bec36647d63c86675d4f4a8eed2478aa89c3fa379b5aa0fb    0.0s
 => => naming to docker.io/library/arg:v1                                                                 0.0s
 => => unpacking to docker.io/library/arg:v1                                                              0.0s


3.233.234.102 | 172.31.70.87 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-70-87 ~/dockerfiles/ARG ]$ docker run -d arg:v1
9ee58c212a17d762c99acff0b1f33ee7123df1c4d55f9dbfd9a12fee7181fe48

3.233.234.102 | 172.31.70.87 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-70-87 ~/dockerfiles/ARG ]$ docker exec -it 9ee bash
[root@9ee58c212a17 /]# env
LANG=C.utf8
HOSTNAME=9ee58c212a17
COURSE=AWS
PWD=/
HOME=/root
TERM=xterm
SHLVL=1
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LESSOPEN=||/usr/bin/lesspipe.sh %s
_=/usr/bin/env
[root@9ee58c212a17 /]# exit
exit
 