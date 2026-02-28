USER WONT GET ROOT ACCESS 



98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ git pull
Already up to date.

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ docker build -t user:v1 .
[+] Building 9.3s (7/7) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 169B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => CACHED [1/3] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => [2/3] RUN dnf install nginx -y                                                                        6.1s
 => [3/3] RUN useradd sivakumar                                                                           0.5s
 => exporting to image                                                                                    2.4s
 => => exporting layers                                                                                   1.9s
 => => exporting manifest sha256:5bacb2b3c61883538403a2510a4f6f382c5cf71f36a7914482899ea14540b46a         0.0s
 => => exporting config sha256:cf2aa1dbe4f20c647bf9cc4380e3dfb518511ca07dea10b826d87eca277270c7           0.0s
 => => exporting attestation manifest sha256:8e779a64034550b70d1136e30c24b022cd59478ec5dc471b011a67bfcab  0.0s
 => => exporting manifest list sha256:a0f3b14344482a11c1eb5b0d8897a06cdd53c9ee7a294427dd741a238be8ec6f    0.0s
 => => naming to docker.io/library/user:v1                                                                0.0s
 => => unpacking to docker.io/library/user:v1                                                             0.4s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ docker run -d user:v1
dcebd428fa6fc5c8cb1a5aae9ec66cd29dcc904a733228052ef8be7cb6d875da

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ docker ps
CONTAINER ID   IMAGE     COMMAND        CREATED         STATUS         PORTS     NAMES
dcebd428fa6f   user:v1   "sleep 1000"   6 seconds ago   Up 5 seconds             epic_lederberg

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ docker exec -it dc bash
[sivakumar@dcebd428fa6f /]$ id
uid=1000(sivakumar) gid=1000(sivakumar) groups=1000(sivakumar)
