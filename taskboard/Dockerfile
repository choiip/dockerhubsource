FROM php:alpine 

LABEL MAINTAINER "Alex Choi" <choiip@gmail.com>

# Prepare system 
ENV PROJECT /var/www/html

RUN apk update \
 && apk upgrade \
 && apk add --no-cache sqlite openjdk8-jre openrc bash \
 && rm -rf /var/cache/apk/*

WORKDIR $PROJECT

# Download project 
RUN curl -L https://api.github.com/repos/kiswa/TaskBoard/tarball | tar xz --strip=1

# Build project 
RUN php build/composer.phar self-update
RUN php build/composer.phar update
RUN php build/composer.phar install
RUN bash ./build/build-all

# Configure project 
RUN chmod -R +w $PROJECT/api/ \
 && chown -R www-data:www-data $PROJECT/
EXPOSE 80

# Cleanning system 
RUN apk del openjdk8-jre openrc bash
# Start instance to service 
CMD ["php", "-S", "0.0.0.0:80", "devrouter.php"]
