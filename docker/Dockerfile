FROM node:16.4.2-buster

# Locales
RUN apt-get update \
	&& apt-get install -y locales

RUN dpkg-reconfigure locales \
	&& locale-gen C.UTF-8 \
	&& /usr/sbin/update-locale LANG=C.UTF-8

RUN echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen \
	&& locale-gen

ENV LC_ALL C.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

# Common
RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
		openssl \
		git \
		gnupg2 \
		vim \
		telnet

# Upgrade YARN
RUN npm i -g yarn -f

# Setup default
RUN mkdir -p /var/www/html \
    && chown -R node:node /var/www

USER node:node
VOLUME /var/www
WORKDIR /var/www/html