FROM centos:7

COPY mongo.repo /etc/yum.repos.d/mongo.repo

RUN yum update -y

RUN yum install -y mongodb-org

RUN mkdir -p /data/db

EXPOSE 27017

ENTRYPOINT ["/usr/bin/mongod"]
