FROM php:8-fpm

ENV NODE_MAJOR=21

# Mise à jour et installation des dépendances nécessaires
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    git \
    && rm -rf /var/lib/apt/lists/*
    
RUN apt update && apt upgrade -y \
    && apt install -y libicu-dev git zip \
    && docker-php-ext-install pdo_mysql intl

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    && mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

RUN apt install -y ca-certificates curl gnupg \
    && mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
    && apt update \
    && apt install -y nodejs

# Installation de Angular CLI
RUN npm install -g @angular/cli

CMD ng serve --host 0.0.0.0 --port 4200

WORKDIR /app