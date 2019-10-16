Docker volumes:
===============

Create volume and mount:

# docker volume create Jenkins
#docker volume inspect jenkins
# docker run -d –name myjenkins -p 8080:8080 -v Jenkins:/var/Jenkins_home Jenkins:latest

Create directory with full permission :

# mkdir backup && chmod -R 777 backup
# docker run -d –name myjenkins2 -p 9090:9090 -v /root/backup:/var/Jenkins_home Jenkins:latest

Container volume  to new container:
# docker run -d --volumes-from myjenkins2 --name myjenkins4 jenkins:latest
# docker run -d --volumes-from myjenkins -p 9090:9090 --name myjenkins2 jenkins:latest

docker cp container1 to container2:
# docker cp index.html <containerid> /bin/bash
# docker export <containerid> | gzip > backup.tar.gz
# zcat backup.tar.gz | docker import – my backup 
