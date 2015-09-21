FROM centos:6.6
MAINTAINER Greg Aumann http://devopsquality.com "devopsquality@gmail.com"
ENV REFRESHED_AT 2015-09-21

# Install ansible
RUN yum -y install epel-release && yum -y install ansible; yum clean all

WORKDIR /opt/ansible

COPY ansible_playbooks/ /opt/ansible/
RUN ansible-playbook site.yml
