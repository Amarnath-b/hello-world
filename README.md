## DevOps Project for Beginners   

[![Image](https://github.com/yankils/Simple-DevOps-Project/blob/master/Devops_course.PNG "DevOps Project - CI/CD with Jenkins Ansible Docker Kubernetes ")](https://www.udemy.com/course/valaxy-devops/?referralCode=8147A5CF4C8C7D9E253F)

Docker file - updated
[root@Docker-Host ~]# vi Dockerfile
FROM centos
RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum install java -y
RUN mkdir /opt/tomcat/
WORKDIR /opt/tomcat
ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz .
RUN tar -xvzf apache-tomcat-9.0.68.tar.gz
RUN mv apache-tomcat-9.0.68/* /opt/tomcat
EXPOSE 8080
CMD ["/opt/tomcat/bin/catalina.sh","run"]


Reference: 
https://techglimpse.com/failed-metadata-repo-appstream-centos-8/
Fix Failed to download metadata for repo
CentOS Linux 8 had reached the End Of Life (EOL) on December 31st, 2021. It means that CentOS 8 will no longer receive development resources from the official CentOS project. After Dec 31st, 2021, if you need to update your CentOS, you need to change the mirrors to vault.centos.org where they will be archived permanently. Alternatively, you may want to upgrade to CentOS Stream.

Step 1: Go to the /etc/yum.repos.d/ directory.

[root@autocontroller ~]# cd /etc/yum.repos.d/
Step 2: Run the below commands

[root@autocontroller ~]# sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
[root@autocontroller ~]# sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
Step 3: Now run the yum update

[root@autocontroller ~]# yum update -y
That’s it!
