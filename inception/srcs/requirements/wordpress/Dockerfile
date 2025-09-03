FROM debian:bullseye

# Gerekli paketler
RUN apt-get update && apt-get install -y \
    php7.4 \
    php7.4-fpm \
    php7.4-mysql \
    curl \
    wget \
    mariadb-client \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Çalışma dizini
WORKDIR /var/www/html

# WordPress indir ve çıkar
RUN curl -o wordpress.tar.gz https://wordpress.org/latest.tar.gz \
    && tar -xvzf wordpress.tar.gz --strip-components=1 \
    && rm wordpress.tar.gz

# PHP-FPM foreground’da çalışacak
CMD ["php-fpm7.4", "-F"]
