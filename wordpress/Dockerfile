# openss-server + Ubuntu 16.04
# maker Kevin
# Version 1.0

From ubuntu:16.04

MAINTAINER Kevin wei <gra230434@gmail.com>

ARG username
ARG userpassword
ENV USER ${username:-user}
ENV USERPW ${userpassword:-000000}

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev && rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install gd mysqli opcache

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

ADD init.sh /root/init.sh
RUN chmod 700 /root/init.sh

EXPOSE 22
CMD ["/root/init.sh"]
