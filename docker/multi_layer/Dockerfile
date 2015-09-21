FROM centos:6.6
MAINTAINER Greg Aumann http://devopsquality.com "devopsquality@gmail.com"
ENV REFRESHED_AT 2015-09-21

# Install ansible
RUN yum -y install epel-release && yum -y install ansible; yum clean all

WORKDIR /opt/ansible

COPY ansible_playbooks/run_role.yml /opt/ansible/run_role.yml

RUN mkdir -p /opt/ansible/roles

COPY ansible_playbooks/roles/common/ /opt/ansible/roles/common
RUN ansible-playbook run_role.yml --extra-vars role=common

COPY ansible_playbooks/group_vars/ /opt/ansible/group_vars
COPY ansible_playbooks/roles/mysql/ /opt/ansible/roles/mysql
RUN ansible-playbook run_role.yml --extra-vars role=mysql

COPY ansible_playbooks/roles/nginx/ /opt/ansible/roles/nginx
RUN ansible-playbook run_role.yml --extra-vars role=nginx

COPY ansible_playbooks/roles/php-fpm/ /opt/ansible/roles/php-fpm
RUN ansible-playbook run_role.yml --extra-vars role=php-fpm

COPY ansible_playbooks/roles/wordpress/ /opt/ansible/roles/wordpress
RUN ansible-playbook run_role.yml --extra-vars role=wordpress
