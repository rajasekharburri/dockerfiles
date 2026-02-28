PRACTICE
-------------
98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ git pull
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 1), reused 6 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 1.40 KiB | 1.40 MiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   b024d27..9dfeaa1  main       -> origin/main
Updating b024d27..9dfeaa1
Fast-forward
 USER/READM.MD      | 42 ++++++++++++++++++++++++++++++++++++++++++
 WORKDIR/Dockerfile |  7 +++++++
 2 files changed, 49 insertions(+)
 create mode 100644 USER/READM.MD
 create mode 100644 WORKDIR/Dockerfile

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/USER ]$ cd ../WORKDIR/

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/WORKDIR ]$ docker build -t work:v1  --no-cache --progress=plain .
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 137B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/almalinux:9
#2 DONE 0.1s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s

#4 [1/3] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d9719192826d4ac
#4 resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d9719192826d4ac 0.0s done
#4 CACHED

#5 [2/3] RUN cd /tmp
#5 DONE 0.3s

#6 [3/3] RUN pwd
#6 0.293 /
#6 DONE 0.3s

#7 exporting to image
#7 exporting layers 0.1s done
#7 exporting manifest sha256:0dd0e29b80b7d4042cea0687fb1fedac8d8f500545b63b5bef090ef270362302 0.0s done
#7 exporting config sha256:aaf726269e49e3f03faa6228e8f3039e9742d51bd3f1eb30525a1d80328e924b 0.0s done
#7 exporting attestation manifest sha256:9909f826be20b99cd8a820e5e3833a6f573821fca416884a79d2d6a673ffa1d2 0.0s done
#7 exporting manifest list sha256:02adc619c4d0df9ee7c79f8d400b3aeacfbc7a1ca1866218d9d47759b2cf3d5a 0.0s done
#7 naming to docker.io/library/work:v1 done
#7 unpacking to docker.io/library/work:v1 done
#7 DONE 0.2s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/WORKDIR ]$ git pull
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 4 (delta 1), reused 4 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 359 bytes | 359.00 KiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   9dfeaa1..7d10adf  main       -> origin/main
Updating 9dfeaa1..7d10adf
Fast-forward
 WORKDIR/Dockerfile | 8 ++++----
 1 file changed, 4 insertions(+), 4 deletions(-)

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/WORKDIR ]$ docker build -t work:v1  --no-cache --progress=plain .
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 135B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/almalinux:9
#2 DONE 0.1s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s

#4 [1/4] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d9719192826d4ac
#4 resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d9719192826d4ac 0.0s done
#4 CACHED

#5 [2/4] RUN mkdir /app
#5 DONE 0.2s

#6 [3/4] WORKDIR /app
#6 DONE 0.0s

#7 [4/4] RUN pwd
#7 0.224 /app
#7 DONE 0.2s

#8 exporting to image
#8 exporting layers 0.1s done
#8 exporting manifest sha256:8f180da98c45139bf4a00a1f0d1ac8eacf37365be24e1d18812edb14fec8b45d 0.0s done
#8 exporting config sha256:0bff8d328010eb745c81ab337a7b1f5759c98754ab1fce0c168bd40fdc3b5b7e 0.0s done
#8 exporting attestation manifest sha256:5f0d1b845cf4207f027d0ae67809e4021d371e75ae3c64e216dadff77828bf66 0.0s done
#8 exporting manifest list sha256:e18c5f278a9e006ca79ef8df07351fea2a11c6faf166b3f2bf7ca5d4e507c76b 0.0s done
#8 naming to docker.io/library/work:v1 done
#8 unpacking to docker.io/library/work:v1 0.1s done
#8 DONE 0.3s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/WORKDIR ]$
