ARG vs ENV
==========
1. ENV is used to supply the key value pairs for the container/runtime
2. ARG is used to supply the values to variables at build time.
3. ARG can't be accessible inside container.

PRACTICE
-------------
98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles ]$ cd ENV

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker build -t rajasekharburri/env:v1 .
[+] Building 5.6s (5/5) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 117B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.3s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => [1/1] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  1.2s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => => sha256:006af5926103913f55c7e1141bf3b8f4fec2f01bf6683700e266d4f3ed45f279 70.42MB / 70.42MB          1.1s
 => exporting to image                                                                                    5.0s
 => => exporting layers                                                                                   0.0s
 => => exporting manifest sha256:4edb12d6dab2412306e28e077c73bb59dc555e7ca8096f6651888834279f739d         0.0s
 => => exporting config sha256:e3638b821b8f8c2a21ff05afee0b8f23704a69a87cb8ff25607bf466f46e21e2           0.0s
 => => exporting attestation manifest sha256:fad2e74f729f9345dbad92c1c976642b11eab6469d5a8ffc5851761c645  0.0s
 => => exporting manifest list sha256:b39a77f303cb42dd94d4acea60df28e47b943b8844cdcd91bd99df45ce88f409    0.0s
 => => naming to docker.io/rajasekharburri/env:v1                                                         0.0s
 => => unpacking to docker.io/rajasekharburri/env:v1                                                      4.4s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker images
                                                                                           i Info →   U  In Use
IMAGE                    ID             DISK USAGE   CONTENT SIZE   EXTRA
rajasekharburri/env:v1   b39a77f303cb        274MB         70.4MB

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker run b39a77f303cb

after change sleep to 1000

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker ps
CONTAINER ID   IMAGE                    COMMAND        CREATED         STATUS         PORTS     NAMES
ac0dca884457   rajasekharburri/env:v1   "sleep 1000"   7 seconds ago   Up 6 seconds             loving_keldysh

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker exec -it ac bash
[root@ac0dca884457 /]# env
Course=Docker
HOSTNAME=ac0dca884457
DURATION=10hrs
PWD=/
TRAINER=SIVA
HOME=/root
LANG=C.utf8
TERM=xterm
LESSOPEN=||/usr/bin/lesspipe.sh %s
SHLVL=1
DEBUGINFOD_IMA_CERT_PATH=/etc/keys/ima:
PATH=/root/.local/bin:/root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/env
[root@ac0dca884457 /]# exit
exit

to over ride

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENV ]$ docker run -d -e Course=DEVOPS  joindevops:v1

