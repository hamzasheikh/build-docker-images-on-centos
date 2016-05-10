Get Started with Building Docker Images on CentOS 7
===================================================

Prerequities
------------

* Vagrant
* Ansible

How
---

Create CentOS VM.

::

    user@host$ vagrant box update
    user@host$ vagrant up
    user@host$ vagrant reload

Build a Docker image.

::

    user@host$ vagrant ssh
    [vagrant@localhost ~]$ docker build docker/mongo

Find built image and run it as a container. IDs used here will change every
time you build an image and they will be different in your environment.

::

    [vagrant@localhost ~]$ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    <none>              <none>              617a8511b77c        18 seconds ago      557 MB
    centos              7                   778a53015523        5 weeks ago         196.7 MB

    [vagrant@localhost ~]$ docker ps
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

    [vagrant@localhost ~]$ docker run -d 617a8511b77c
    fd1a2774120b2230d6d27f3f76c90603245160991314b3779464d8ae410c4321

    [vagrant@localhost ~]$ docker ps
    CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS               NAMES
    fd1a2774120b        617a8511b77c        "/usr/bin/mongod"   About a minute ago   Up About a minute   27017/tcp           condescending_archimedes
