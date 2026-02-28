ADD
===
ADD is also like COPY to copy the content inside the image. But ADD has 2 extra capabilities

1. It can directly fetch the content from internet
2. It can directly untar the file inside container/image


PRACTICE
-------------
98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ git pull
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 8 (delta 4), reused 7 (delta 3), pack-reused 0 (from 0)
Unpacking objects: 100% (8/8), 662 bytes | 662.00 KiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   5e249a8..129b4d1  main       -> origin/main
Updating 5e249a8..129b4d1
Fast-forward
 ADD/Dockerfile | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker build -t add:v1 .
[+] Building 0.6s (7/7) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 181B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => [2/2] ADD https://raw.githubusercontent.com/daws-86s/notes/refs/heads/main/session-53.txt /tmp/sessi  0.1s
 => CACHED [1/2] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => [2/2] ADD https://raw.githubusercontent.com/daws-86s/notes/refs/heads/main/session-53.txt /tmp/sessi  0.0s
 => exporting to image                                                                                    0.2s
 => => exporting layers                                                                                   0.1s
 => => exporting manifest sha256:fad66b737c2ca7556659cb2c09118201957e28ee88eae6f41c068eeffb562a9f         0.0s
 => => exporting config sha256:3cadc721929e6d678b1ae6da76ff98b3382278a7041e0a8cd7edd4527a63f941           0.0s
 => => exporting attestation manifest sha256:43f840cf38bf7a7247c5785ffcb844d0514f1564090c387c51ab6d7c485  0.0s
 => => exporting manifest list sha256:f839bed9b428d7e81cd18ad2dbaee823010d1fe9acb5d52002edbffdca80888d    0.0s
 => => naming to docker.io/library/add:v1                                                                 0.0s
 => => unpacking to docker.io/library/add:v1                                                              0.0s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docke rps
-bash: docke: command not found

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docke run -d add:v1
-bash: docke: command not found

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker run -d add:v1
c8dd2e47c738693f9579542654c250e6cae55c06fbddeae173649db33257d70e

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker ps
CONTAINER ID   IMAGE     COMMAND        CREATED         STATUS         PORTS     NAMES
c8dd2e47c738   add:v1    "sleep 1000"   5 seconds ago   Up 5 seconds             festive_hawking

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker exec -it c8 bash
[root@c8dd2e47c738 /]# env
HOSTNAME=c8dd2e47c738
PWD=/
HOME=/root
LANG=C.utf8
TERM=xterm
LESSOPEN=||/usr/bin/lesspipe.sh %s
SHLVL=1
DEBUGINFOD_IMA_CERT_PATH=/etc/keys/ima:
PATH=/root/.local/bin:/root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
_=/usr/bin/env
[root@c8dd2e47c738 /]# cd/tmp/
bash: cd/tmp/: No such file or directory
[root@c8dd2e47c738 /]# cd /tmp/
[root@c8dd2e47c738 tmp]# ls -l
total 4
-rw------- 1 root root 1705 Jan  1  1970 session-53.txt
[root@c8dd2e47c738 tmp]# cat session-53.txt
Notes
#!/bin/bash
[root@c8dd2e47c738 tmp]# exit
exit


ADDing tar file

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ git pull
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 2), reused 6 (delta 2), pack-reused 0 (from 0)
Unpacking objects: 100% (6/6), 1.05 MiB | 18.82 MiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   129b4d1..7a8e219  main       -> origin/main
Updating 129b4d1..7a8e219
Fast-forward
 ADD/Dockerfile   |   1 +
 ADD/README.MD    |  82 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 ADD/sample-1.tar | Bin 0 -> 1101824 bytes
 3 files changed, 83 insertions(+)
 create mode 100644 ADD/sample-1.tar

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker build -t add:v1 .
[+] Building 0.7s (9/9) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 204B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => [2/3] ADD https://raw.githubusercontent.com/daws-86s/notes/refs/heads/main/session-53.txt /tmp/sessi  0.1s
 => [internal] load build context                                                                         0.1s
 => => transferring context: 1.10MB                                                                       0.0s
 => [1/3] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => CACHED [2/3] ADD https://raw.githubusercontent.com/daws-86s/notes/refs/heads/main/session-53.txt /tm  0.0s
 => [3/3] ADD sample-1.tar /tmp/                                                                          0.0s
 => exporting to image                                                                                    0.3s
 => => exporting layers                                                                                   0.1s
 => => exporting manifest sha256:c2a75eb2237ee6c4b2d3fe80060d8fc38e44adfd5369a2207bae4065e6a8b096         0.0s
 => => exporting config sha256:cf145b9bbfe2e358f2ed34e99187a2f4691c0ee2c2eebefda47324126f9e42de           0.0s
 => => exporting attestation manifest sha256:3402d8bf5c51876afec4f60816ceeeb45f71476a20fbdbad49973b9235f  0.0s
 => => exporting manifest list sha256:0b54c98edcdf49bb9770e55cc8163b85802a572bdb2641fe705c500d8a91da49    0.0s
 => => naming to docker.io/library/add:v1                                                                 0.0s
 => => unpacking to docker.io/library/add:v1                                                              0.0s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker run -d add:v1
1f50949394272d11d75f29b8c231f759233b68a083264cc3279b1d711c66aaa4

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ADD ]$ docker exec -it 1f  bash
[root@1f5094939427 /]# cd / tmp/
bash: cd: too many arguments
[root@1f5094939427 /]# cd /tmp/
[root@1f5094939427 tmp]# ls -l
total 4
drwxrwxrwx 2 root root   95 Dec 31  2022 sample-1
-rw------- 1 root root 1705 Jan  1  1970 session-53.txt
[root@1f5094939427 tmp]# cd sample-1/
[root@1f5094939427 sample-1]# ls -l
total 1080
-rwxrwxrwx 1 root root 361666 Dec 30  2022  sample-1.webp
-rwxrwxrwx 1 root root 361666 Dec 30  2022  sample-1_1.webp
-rwxrwxrwx 1 root root 214895 Dec 31  2022 'sample-5 (1).jpg'
-rwxrwxrwx 1 root root 159068 Dec 30  2022  sample-5.webp
[root@1f5094939427 sample-1]#
