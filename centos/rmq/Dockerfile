FROM centos:centos7.9.2009

USER root

RUN yum -y install epel-release
RUN yum -y update
RUN yum -y install erlang socat wget

RUN wget https://www.rabbitmq.com/releases/rabbitmq-server/v3.6.10/rabbitmq-server-3.6.10-1.el7.noarch.rpm
RUN rpm --import https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
RUN rpm -Uvh rabbitmq-server-3.6.10-1.el7.noarch.rpm

RUN systemctl start rabbitmq-server

RUN systemctl stop firewalld

RUN rabbitmq-plugins enable rabbitmq_management
RUN chown -R rabbitmq:rabbitmq /var/lib/rabbitmq/
RUN rabbitmqctl add_user admin StrongPassword
RUN rabbitmqctl set_user_tags admin administrator
RUN rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"