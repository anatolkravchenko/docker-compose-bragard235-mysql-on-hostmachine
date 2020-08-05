FROM php:7.2-fpm
#FROM devilbox/php-fpm-7.4:latest

RUN apt-get update \
&& apt-get install -y \
libxml2 \
libxml2-dev \
curl \
wget \
git \
libfreetype6-dev \
libjpeg62-turbo-dev \
libpng-dev \
libxslt1.1 \
libxslt-dev \
telnet \
gulp \
npm

RUN npm install --global gulp-cli
RUN npm install gulp-multi-dest  
RUN npm install gulp-logger
RUN npm install gulp-plumber
RUN npm install gulp-notify
RUN npm install browser-sync
RUN npm install gulp-rimraf
RUN npm install stylelint
RUN npm install gulp-postcss
RUN npm install gulp-replace
RUN npm install gulp-sass-lint
RUN npm install gulp-sass 
RUN npm install cssnano
RUN npm install gulp-svg-sprite
RUN npm install marked-terminal


RUN apt-get install -y libonig-dev libzip-dev libmcrypt-dev libicu-dev

RUN pecl install mcrypt-1.0.3 
RUN docker-php-ext-enable mcrypt 

#RUN docker-php-ext-install -j$(nproc) iconv gd intl mcrypt mbstring mysqli pdo_mysql soap zip bcmath xsl

RUN docker-php-ext-install bcmath
RUN docker-php-ext-install intl 
RUN docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql soap zip
RUN docker-php-ext-install xsl

#RUN docker-php-ext-configure gd --with-freetype --with-jpeg 
#RUN docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/;
RUN docker-php-ext-install gd


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www

CMD ["php-fpm"]

