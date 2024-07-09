# Utilisez l'image de base Debian
FROM debian:bullseye

# Installation de BIND9
RUN apt-get update && \
    apt-get install -y bind9 bind9utils bind9-doc && \
    rm -rf /var/lib/apt/lists/*

# # Définir le répertoire de travail
# WORKDIR /etc/bind

# Copie des fichiers de configuration BIND
COPY named.conf /etc/bind/named.conf
COPY named.conf.options /etc/bind/named.conf.options
COPY named.conf.local /etc/bind/named.conf.local
COPY db.example.com /etc/bind/db.example.com

# Exposition des ports DNS standard (53/tcp et 53/udp)
EXPOSE 53/tcp 53/udp

# Commande pour démarrer BIND9
CMD ["named", "-g", "-c", "/etc/bind/named.conf"]

