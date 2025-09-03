FROM debian:bullseye

# MariaDB kurulumu
RUN apt-get update && apt-get install -y mariadb-server \
    && rm -rf /var/lib/apt/lists/*

# Config klasörünü kopyala (opsiyonel)
COPY ./conf/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf

# Init scriptleri container başlarken çalıştırılacak
COPY ./tools/ /docker-entrypoint-initdb.d/

# Ortam değişkenlerini kullan (docker-compose -> .env)
ENV MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
ENV MYSQL_DATABASE=${MYSQL_DATABASE}
ENV MYSQL_USER=${MYSQL_USER}
ENV MYSQL_PASSWORD=${MYSQL_PASSWORD}

# Veritabanı klasörü
VOLUME /var/lib/mysql

# Container başlarken MariaDB'yi foreground'da çalıştır
CMD ["mysqld_safe"]
