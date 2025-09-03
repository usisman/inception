FROM debian:bullseye

# Gerekli paketler
RUN apt-get update && apt-get install -y \
    nginx \
    openssl \
    && rm -rf /var/lib/apt/lists/*

# SSL sertifikası üret
RUN mkdir -p /etc/nginx/ssl && \
    openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/nginx.key \
    -out /etc/nginx/ssl/nginx.crt \
    -subj "/C=TR/ST=Istanbul/L=Istanbul/O=42/OU=student/CN=${DOMAIN_NAME}"

# NGINX konfigürasyonunu kopyala
COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf

# Çalışma dizini
WORKDIR /var/www/html

# NGINX foreground’da çalışacak
CMD ["nginx", "-g", "daemon off;"]
