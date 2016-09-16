FROM ubuntu
MAINTAINER Robert Porter Version 0.2

ENV DEBIAN_FRONTEND noninteractive
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup
RUN echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache
RUN echo $'#!/bin/sh\nexit 101' > /usr/sbin/policy-rc.d
RUN chmod +x /usr/sbin/policy-rc.d

RUN \
  apt-get update && \
  apt-get -y install \
	  software-properties-common \
          vim \
          pwgen \
          unzip \
          curl \
          git-core \
	  libapache2-mod-php5 \
          php5-mysql \
          mysql-client-5.5 \
          apache2 && \
  rm /var/www/html/index.html && \
  rm -rf /var/lib/apt/lists/*

ENV WP_PASS wordpress
ENV WP_USER wordpress
ENV WP_DB wordpress
ENV APP_ROOT /var/www/html

ADD http://wordpress.org/latest.tar.gz wordpress.tar.gz

RUN \
  tar xzf wordpress.tar.gz -C ${APP_ROOT} --strip-components 1 && \
  rm wordpress.tar.gz

COPY start.sh start.sh

VOLUME ["$APP_ROOT"]

RUN rm /usr/sbin/policy-rc.d
CMD ["/start.sh"]

EXPOSE 80
