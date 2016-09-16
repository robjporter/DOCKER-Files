# A basic apache server with PHP. To use either add or bind mount content under /var/www

FROM ubuntu:12.04

MAINTAINER Robert Porter version: 0.4

RUN apt-get update && apt-get install -y apache2
RUN apt-get install -y php5 libapache2-mod-php5 php5-mysql php5-cli
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
RUN rm -f /var/www/index.html
RUN echo "<?= phpinfo() ?>" >> /var/www/index.php

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

EXPOSE 80

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
