FROM php:8.1-fpm

# Install system dependencies and PHP extensions
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql opcache

# Enable OPcache with recommended settings
RUN echo "opcache.enable=1\n" \
         "opcache.memory_consumption=128\n" \
         "opcache.interned_strings_buffer=8\n" \
         "opcache.max_accelerated_files=4000\n" \
         "opcache.revalidate_freq=2\n" \
         "opcache.validate_timestamps=1\n" \
         > /usr/local/etc/php/conf.d/opcache-recommended.ini
