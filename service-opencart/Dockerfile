FROM php:8.1-apache

LABEL maintainer="seuemail@exemplo.com"
LABEL description="Imagem Docker para rodar OpenCart com Apache e PHP"

RUN apt-get update && apt-get install -y \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libxml2-dev \
    libicu-dev \
    libbz2-dev \
    unzip \
    zip \
    git \
    curl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        zip \
        gd \
        mbstring \
        pdo \
        mysqli \
        intl \
        xml \
        bz2 \
        opcache \
    && apt-get clean

RUN a2enmod rewrite

WORKDIR /var/www/html

# Baixa e extrai o OpenCart (ex: versão 4.0.2.3)
ADD https://github.com/boraMnis/docker-swarm-experiments/

# Descompacta o arquivo zip manualmente
RUN unzip /tmp/opencart.zip -d /var/www/html && \
    rm /tmp/opencart.zip

RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

EXPOSE 80

CMD ["apache2-foreground"]
