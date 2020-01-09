FROM ubuntu:18.04
FROM python:3.8.1

maintainer mathpresso

# use mirror
RUN cd /etc/apt && \
  sed -i 's/deb.debian.org/ftp.daum.net/g' sources.list

# install nginx
RUN \
  apt-get update && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  rm /etc/nginx/sites-enabled/default && \
  chown -R www-data:www-data /var/lib/nginx

# install some packages for python/django/nginx/supervisor
RUN apt-get update
RUN apt-get install -y build-essential git
RUN apt-get install -y python python-dev python-setuptools

# install mysql_config
RUN apt-get install -y default-libmysqlclient-dev

# install supervisor
RUN apt-get install -y supervisor

# install uwsgi
RUN apt-get install -y python3-pip
RUN pip3 install uwsgi
