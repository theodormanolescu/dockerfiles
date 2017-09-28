############################################################
# Dockerfile to build a basic container image
# Based on centos7
############################################################
FROM centos:centos7
VOLUME ["/sys/fs/cgroup", "/run", "/tmp"]
MAINTAINER theodor.manolescu@emag.ro

# systemd (Source: https://github.com/docker-library/docs/tree/master/centos#systemd-integration)
ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y --setopt=tsflags=nodocs update && \
    yum -y --setopt=tsflags=nodocs install wget vim nano htop git && \
    yum clean all

EXPOSE 22 80 8000 3306 443

CMD ["/usr/sbin/init"]