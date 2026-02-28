FROM almalinux:9
RUN dnf install nginx -y
RUN useradd sivakumar

USER sivakumar 
#user wont get root access

CMD ["sleep", "1000"]