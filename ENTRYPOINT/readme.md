CMD ENTRYPOINT
==========
1. CMD instruction can be overriden.
2. ENTRYPOINT can't be overriden, if we try it will go and append that leads to failure
3. CMD can be used to supply the default args to ENTRYPOINT. You can always override the default args at run time

PRACTICE
-------------
98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker build -t entry:v1 .
[+] Building 0.5s (5/5) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 79B                                                                       0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => CACHED [1/1] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => exporting to image                                                                                    0.1s
 => => exporting layers                                                                                   0.0s
 => => exporting manifest sha256:35197766be44b16c5b09256bc0a924383bf6d58e46826b7a0d092453423d4c7e         0.0s
 => => exporting config sha256:d04d029f309bd9e3518f9877b505074e5299ea36fd0d5bd0f677c40c86e231ec           0.0s
 => => exporting attestation manifest sha256:77a5a593ea8aa9f32286a9ed9f0bdd45ff8eb0c0a326e7c21874ec83e00  0.0s
 => => exporting manifest list sha256:78cfb86b9e73c0b22fbd9b2002f0462e72db9ffe36f44f81f5adb44ec5d341e1    0.0s
 => => naming to docker.io/library/entry:v1                                                               0.0s
 => => unpacking to docker.io/library/entry:v1                                                            0.0s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1
PING google.com (64.233.180.139) 56(84) bytes of data.
64 bytes from pe-in-f139.1e100.net (64.233.180.139): icmp_seq=1 ttl=105 time=1.94 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=2 ttl=105 time=1.99 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=3 ttl=105 time=2.02 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=4 ttl=105 time=2.02 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=5 ttl=105 time=2.04 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=6 ttl=105 time=2.00 ms
64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=7 ttl=105 time=2.02 ms
^C64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=8 ttl=105 time=2.00 ms
^X64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=9 ttl=105 time=1.98 ms
^Z64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=10 ttl=105 time=2.08 ms
^Z64 bytes from on-in-f139.1e100.net (64.233.180.139): icmp_seq=11 ttl=105 time=2.12 ms
^X^C
--- google.com ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10016ms
rtt min/avg/max/mdev = 1.937/2.018/2.122/0.047 ms

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1 ping facebook.com
PING facebook.com (31.13.66.35) 56(84) bytes of data.
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=1 ttl=54 time=1.18 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=2 ttl=54 time=1.22 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=3 ttl=54 time=1.23 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=4 ttl=54 time=1.23 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=5 ttl=54 time=1.22 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=6 ttl=54 time=1.23 ms
^C
--- facebook.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5008ms
rtt min/avg/max/mdev = 1.183/1.218/1.233/0.016 ms

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ git pull
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 1), reused 5 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (5/5), 545 bytes | 545.00 KiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   2ccb87f..4d1c6fc  main       -> origin/main
Updating 2ccb87f..4d1c6fc
Fast-forward
 ENTRYPOINT/Dockerfile | 3 ++-
 ENTRYPOINT/readme.md  | 5 +++++
 2 files changed, 7 insertions(+), 1 deletion(-)
 create mode 100644 ENTRYPOINT/readme.md

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker build -t entry:v1 .
[+] Building 0.5s (5/5) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 91B                                                                       0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => CACHED [1/1] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => exporting to image                                                                                    0.1s
 => => exporting layers                                                                                   0.0s
 => => exporting manifest sha256:86d418bf8e1c1195707d325ef029713abc9fc20be8303ed227ba8baf4d1dc992         0.0s
 => => exporting config sha256:c67650beb82986eab0466bd8974d8f84f2298297a85abf72554e37c0cd21db6e           0.0s
 => => exporting attestation manifest sha256:29cca256e5b675b8d81cab1edb2b0597c3d0b0d2af7aafc13fa48669d34  0.0s
 => => exporting manifest list sha256:15250afc290935bc7a302fe242cfae6fef7a77329065e4bb1ee9c525b16dca31    0.0s
 => => naming to docker.io/library/entry:v1                                                               0.0s
 => => unpacking to docker.io/library/entry:v1                                                            0.0s

 1 warning found (use docker --debug to expand):
 - JSONArgsRecommended: JSON arguments recommended for ENTRYPOINT to prevent unintended behavior related to OS signals (line 3)

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ git pull
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 4 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 372 bytes | 372.00 KiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   4d1c6fc..3717bb9  main       -> origin/main
Updating 4d1c6fc..3717bb9
Fast-forward
 ENTRYPOINT/Dockerfile | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker build -t entry:v1 .
[+] Building 0.4s (5/5) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 114B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => CACHED [1/1] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => exporting to image                                                                                    0.1s
 => => exporting layers                                                                                   0.0s
 => => exporting manifest sha256:2013889011b9355b1779e7aaf724e221952df699b4724bf454b2471b91b853a8         0.0s
 => => exporting config sha256:d58a0dc67ebe23319b44fe17856893ba7c8d3488950518177c56ef757bf4c0ac           0.0s
 => => exporting attestation manifest sha256:358055f7cb5078e2323b136b2acd308849d700a6ba77f072d1e42d2a1c8  0.0s
 => => exporting manifest list sha256:d407af2090890004aba6812960733752aa30e772139634b0db4efb12bebe77bc    0.0s
 => => naming to docker.io/library/entry:v1                                                               0.0s
 => => unpacking to docker.io/library/entry:v1                                                            0.0s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1
PING google.com (64.233.180.113) 56(84) bytes of data.
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=1 ttl=105 time=2.07 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=2 ttl=105 time=2.12 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=3 ttl=105 time=2.09 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=4 ttl=105 time=2.12 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=5 ttl=105 time=2.12 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=6 ttl=105 time=2.12 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=7 ttl=105 time=2.11 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=8 ttl=105 time=2.11 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=9 ttl=105 time=2.15 ms
64 bytes from on-in-f113.1e100.net (64.233.180.113): icmp_seq=10 ttl=105 time=2.13 ms
^C
--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9014ms
rtt min/avg/max/mdev = 2.068/2.113/2.154/0.021 ms

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1 ping facebook.com
ping: ping: Name or service not known

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker ps -a
CONTAINER ID   IMAGE                    COMMAND                  CREATED          STATUS                      PORTS     NAMES
f422173ea627   entry:v1                 "ping google.com pin…"   27 seconds ago   Exited (2) 26 seconds ago             strange_bell
e6d0782bc499   entry:v1                 "ping google.com"        48 seconds ago   Exited (0) 37 seconds ago             laughing_edison
3c93a6a8f6b3   78cfb86b9e73             "ping facebook.com"      5 minutes ago    Exited (0) 5 minutes ago              exciting_cerf
05869bbffbbb   78cfb86b9e73             "ping google.com"        6 minutes ago    Exited (0) 6 minutes ago              busy_dhawan
1f5094939427   add:v1                   "sleep 1000"             13 minutes ago   Up 12 minutes                         angry_gates
c8dd2e47c738   f839bed9b428             "sleep 1000"             19 minutes ago   Exited (0) 2 minutes ago              festive_hawking
ac0dca884457   rajasekharburri/env:v1   "sleep 1000"             37 minutes ago   Exited (0) 20 minutes ago             loving_keldysh
5e8c7a2043f2   8b7676478d12             "sleep 15"               38 minutes ago   Exited (0) 38 minutes ago             hopeful_goldberg
63ce405bdb38   8b7676478d12             "sleep 15"               38 minutes ago   Exited (0) 38 minutes ago             great_bohr
c6f41eddfcff   8b7676478d12             "sleep 15"               40 minutes ago   Exited (0) 40 minutes ago             cool_aryabhata
7602e59014a4   8b7676478d12             "sleep 15"               43 minutes ago   Exited (0) 42 minutes ago             happy_swartz
5d35b596cff7   b39a77f303cb             "/bin/bash"              47 minutes ago   Exited (0) 47 minutes ago             dazzling_engelbart

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker ps -a --notrunk
unknown flag: --notrunk

Usage:  docker ps [OPTIONS]

Run 'docker ps --help' for more information

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker ps -a --no trunc
unknown flag: --no

Usage:  docker ps [OPTIONS]

Run 'docker ps --help' for more information

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker ps -a --no-trunc
CONTAINER ID                                                       IMAGE                                                                     COMMAND                               CREATED              STATUS                          PORTS     NAMES
f422173ea627a521458baa6112ffd1cb73cf196fd59a3324046c18703bdfd4eb   entry:v1                                                                  "ping google.com ping facebook.com"   About a minute ago   Exited (2) About a minute ago             strange_bell
e6d0782bc499a11d8b51fda00de999bbe4c5535393c97e20f6a70cc3ba5ac3f9   entry:v1                                                                  "ping google.com"                     About a minute ago   Exited (0) About a minute ago             laughing_edison
3c93a6a8f6b34ce6882ad920445f6d42d30795ee914c71676a0324a10ed3623b   sha256:78cfb86b9e73c0b22fbd9b2002f0462e72db9ffe36f44f81f5adb44ec5d341e1   "ping facebook.com"                   6 minutes ago        Exited (0) 6 minutes ago                  exciting_cerf
05869bbffbbb458dbc65a1fa29bcefe5494f7dbf93509cc43aca65aef49572c6   sha256:78cfb86b9e73c0b22fbd9b2002f0462e72db9ffe36f44f81f5adb44ec5d341e1   "ping google.com"                     7 minutes ago        Exited (0) 7 minutes ago                  busy_dhawan
1f50949394272d11d75f29b8c231f759233b68a083264cc3279b1d711c66aaa4   add:v1                                                                    "sleep 1000"                          13 minutes ago       Up 13 minutes                             angry_gates
c8dd2e47c738693f9579542654c250e6cae55c06fbddeae173649db33257d70e   sha256:f839bed9b428d7e81cd18ad2dbaee823010d1fe9acb5d52002edbffdca80888d   "sleep 1000"                          20 minutes ago       Exited (0) 3 minutes ago                  festive_hawking
ac0dca8844577bd8fd3dfc396ddd2d8de464cc6752be9041b74c2816786c2690   rajasekharburri/env:v1                                                    "sleep 1000"                          38 minutes ago       Exited (0) 21 minutes ago                 loving_keldysh
5e8c7a2043f2f278b53a2799ad2c14dcf00832079a25fd9332d26f312e820007   sha256:8b7676478d126983fc72326cc3c09c8ced42d9a69b8f7c289d8d1374e5f4b248   "sleep 15"                            39 minutes ago       Exited (0) 39 minutes ago                 hopeful_goldberg
63ce405bdb38268a6a25250a578dc12636889346111e50ef3c0504496224677f   sha256:8b7676478d126983fc72326cc3c09c8ced42d9a69b8f7c289d8d1374e5f4b248   "sleep 15"                            39 minutes ago       Exited (0) 39 minutes ago                 great_bohr
c6f41eddfcffac0e7bc7efad777944f9be0007e434d34eacc801d447a0833e8c   sha256:8b7676478d126983fc72326cc3c09c8ced42d9a69b8f7c289d8d1374e5f4b248   "sleep 15"                            41 minutes ago       Exited (0) 40 minutes ago                 cool_aryabhata
7602e59014a40392e9dacdcd3f0592ff7135f0fa0242673ee2ed1973e7b3e252   sha256:8b7676478d126983fc72326cc3c09c8ced42d9a69b8f7c289d8d1374e5f4b248   "sleep 15"                            43 minutes ago       Exited (0) 43 minutes ago                 happy_swartz
5d35b596cff7f10727d8e1eef5a97939ae9e3f111a542c9ca4673881523a7455   sha256:b39a77f303cb42dd94d4acea60df28e47b943b8844cdcd91bd99df45ce88f409   "/bin/bash"                           48 minutes ago       Exited (0) 48 minutes ago                 dazzling_engelbart

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ git pull
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 4 (delta 1), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 385 bytes | 385.00 KiB/s, done.
From https://github.com/rajasekharbi/dockerfiles
   3717bb9..7dd0325  main       -> origin/main
Updating 3717bb9..7dd0325
Fast-forward
 ENTRYPOINT/Dockerfile | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker build -t entry:v1 .
[+] Building 0.5s (5/5) FINISHED                                                                docker:default
 => [internal] load build definition from Dockerfile                                                      0.0s
 => => transferring dockerfile: 155B                                                                      0.0s
 => [internal] load metadata for docker.io/library/almalinux:9                                            0.1s
 => [internal] load .dockerignore                                                                         0.0s
 => => transferring context: 2B                                                                           0.0s
 => CACHED [1/1] FROM docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c4  0.0s
 => => resolve docker.io/library/almalinux:9@sha256:9c869fd1056a929a1a6c6811a991b5dcb7a1ccfb8e8c44165d97  0.0s
 => exporting to image                                                                                    0.1s
 => => exporting layers                                                                                   0.0s
 => => exporting manifest sha256:78858c091232b0779a74494a881e1f9bf132bb4657006484296217d376300327         0.0s
 => => exporting config sha256:11cd72835e869667bb58f48994ed000b69c3b4a7f33b16ed6aaa55b95772731e           0.0s
 => => exporting attestation manifest sha256:b653ea493722af2e1050f6015007b9b26e89b803a1b111c671017ddecd7  0.0s
 => => exporting manifest list sha256:da25f09f09d8beabfbbec1a42c4f405fe215a30e50c9e853d00d523eadc58df5    0.0s
 => => naming to docker.io/library/entry:v1                                                               0.0s
 => => unpacking to docker.io/library/entry:v1                                                            0.0s

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1 ping facebook.com
ping: ping: Name or service not known

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$ docker run entry:v1  facebook.com
PING facebook.com (31.13.66.35) 56(84) bytes of data.
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=1 ttl=54 time=1.16 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=2 ttl=54 time=1.22 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=3 ttl=54 time=1.20 ms
64 bytes from edge-star-mini-shv-01-iad3.facebook.com (31.13.66.35): icmp_seq=4 ttl=54 time=1.20 ms
^C
--- facebook.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.162/1.196/1.217/0.020 ms

98.93.25.109 | 172.31.73.177 | t3.micro | https://github.com/rajasekharbi/dockerfiles.git
[ ec2-user@ip-172-31-73-177 ~/dockerfiles/ENTRYPOINT ]$
