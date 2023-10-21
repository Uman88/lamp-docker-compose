FROM php:8.1-apache

# Timezone
#RUN echo "Europe/Kyiv" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata
ENV TZ "Europe/Kyiv"

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable apache2 modules
RUN a2enmod rewrite

#
RUN if command -v a2enmod >/dev/null 2>&1; then \
         a2enmod rewrite headers \
     ;fi

#
WORKDIR /var/www/html
RUN chmod -R 755 /var/www/html

# Update
RUN apt -y update --fix-missing && \
     apt upgrade -y && \
     apt --no-install-recommends install -y apt-utils && \
     rm -rf /var/lib/apt/lists/*


# Install useful tools and install important libaries
RUN apt -y update && \
     apt -y --no-install-recommends install nano wget \
 dialog \
 libsqlite3-dev \
 libsqlite3-0 && \
     apt -y --no-install-recommends install default-mysql-client \
 zlib1g-dev \
 libzip-dev \
 libicu-dev && \
     apt -y --no-install-recommends install --fix-missing apt-utils \
 build-essential \
 git \
 curl \
 libonig-dev && \
     apt install -y iputils-ping && \
     apt -y --no-install-recommends install --fix-missing libcurl4 \
 libcurl4-openssl-dev \
 zip \
 openssl && \
     rm -rf /var/lib/apt/lists/*

# Other PHP8 Extensions
 RUN docker-php-ext-install pdo_mysql && \
     docker-php-ext-install bcmath && \
     docker-php-ext-install mysqli && \
     docker-php-ext-install curl && \
     docker-php-ext-install zip && \
     docker-php-ext-install -j$(nproc) intl && \
     docker-php-ext-install mbstring && \
     docker-php-ext-install gettext && \
     docker-php-ext-install calendar && \
     docker-php-ext-install exif

# Cleanup
RUN rm -rf /usr/src/*