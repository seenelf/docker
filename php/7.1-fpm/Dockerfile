FROM chialab/php-dev:7.1-fpm

# Install Mysql Client
RUN apt-get update \
    && apt-get install mysql-client -y \
    && rm -r /var/lib/apt/lists/*