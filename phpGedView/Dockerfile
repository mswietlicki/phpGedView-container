FROM php:8.0-apache

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

RUN apt-get update -y && apt-get install -y \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libxpm-dev \
    libfreetype6-dev

RUN docker-php-ext-configure gd --enable-gd --with-jpeg --with-webp --with-freetype
RUN docker-php-ext-install -j$(nproc) gd pdo_mysql

RUN apt-get install -y libarchive-tools
RUN curl -sSL "https://sourceforge.net/code-snapshots/svn/p/ph/phpgedview/svn/phpgedview-svn-r7369-trunk-phpGedView.zip" | \
    bsdtar xvf - --strip-components=1 -C /var/www/html

RUN usermod --non-unique --uid 1000 www-data \
  && groupmod --non-unique --gid 1000 www-data \
  && chown -R www-data:www-data /var/www
USER www-data