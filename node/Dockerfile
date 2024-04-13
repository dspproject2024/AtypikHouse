# Utilisation d'une image de base Nginx
FROM nginx:latest

# Mise à jour et installation des dépendances nécessaires
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    git \
    && rm -rf /var/lib/apt/lists/*

# Installation de la version 21 de Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_21.x | bash - \
    && apt-get install -y nodejs

# Installation de Angular CLI
RUN npm install -g @angular/cli

# Exposition du port 8082
EXPOSE 8082
