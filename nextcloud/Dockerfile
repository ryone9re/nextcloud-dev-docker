FROM ubuntu:focal

ARG DEBIAN_FRONTEND=noninteractive

# PHP
RUN apt-get update -y
RUN apt-get install --no-install-recommends -y \
  php7.4 \
  php7.4-gd \
  php7.4-zip \
  php7.4-curl \
  php7.4-xml \
  php7.4-mbstring \
  php7.4-mysql \
  php7.4-xdebug \
  php7.4-intl \
  php7.4-imagick \
  php7.4-gmp \
  php7.4-apcu \
  php7.4-bcmath \
  libmagickcore-6.q16-3-extra \
  curl \
  vim \
  lsof \
  make \
  wget \
  unzip \
  xz-utils

RUN echo "xdebug.remote_enable = 1" >> /etc/php/7.4/cli/conf.d/20-xdebug.ini
RUN echo "xdebug.remote_autostart = 1" >> /etc/php/7.4/cli/conf.d/20-xdebug.ini

# Nodejs and npm
RUN wget --no-check-certificate https://nodejs.org/dist/v16.13.1/node-v16.13.1-linux-x64.tar.xz
RUN tar xvf node-v16.13.1-linux-x64.tar.xz
RUN mv node-v16.13.1-linux-x64 /usr/local/bin/node
ENV PATH $PATH:/usr/local/bin/node/bin

# Docker
RUN apt-get -y install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"
RUN apt-get update -y
RUN apt-get install -y docker-ce docker-ce-cli containerd.io
RUN ln -s /var/run/docker-host.sock /var/run/docker.sock

# Nextcloud
WORKDIR /var/www
RUN wget https://download.nextcloud.com/server/releases/nextcloud-22.2.3.zip
RUN unzip nextcloud-22.2.3.zip
RUN rm -rf nextcloud-22.2.3.zip

# Start
WORKDIR /var/www/nextcloud
EXPOSE 8080
ENTRYPOINT [ "php", "-S", "0.0.0.0:8080" ]
