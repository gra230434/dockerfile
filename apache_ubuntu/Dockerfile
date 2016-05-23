# openss-server + Ubuntu 16.04
# maker Kevin
# Version 1.0

From ubuntu:16.04

MAINTAINER Kevin wei <gra230434@gmail.com>

RUN apt-get update && apt-get install -y apache2
RUN mkdir /var/run/sshd

# add a new user
RUN useradd -m ${USER}
RUN echo "${USER}:${USERPW}" | chpasswd

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

ADD init.sh /root/init.sh
RUN chmod 700 /root/init.sh

EXPOSE 22
CMD ["/root/init.sh"]
