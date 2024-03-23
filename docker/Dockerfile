FROM php:fpm

# Install dependencies required for Composer + VIM
RUN apt-get update && apt-get install -y git unzip vim

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set the Composer home directory
ENV COMPOSER_HOME=/usr/local/share/composer

# Add composer global bin directory to PATH, so the installed packages are available system-wide
ENV PATH="${PATH}:$COMPOSER_HOME/vendor/bin"

# Install PHP's MySQL PDO extension
RUN docker-php-ext-install pdo pdo_mysql

# Set work directory to override the `/var/www/html` default
WORKDIR /var/www

# Change to a specific non-root user
USER www-data
