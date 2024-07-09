# Utilisez l'image de base Debian
FROM debian:bullseye

# Installation du serveur DHCP
RUN apt-get update && \
    apt-get install -y isc-dhcp-server && \
    rm -rf /var/lib/apt/lists/*

# # Définir le répertoire de travail
# WORKDIR /etc/dhcp

# Copie de la configuration DHCP
COPY dhcpd.conf /etc/dhcp/dhcpd.conf

# Création du fichier de base de données des baux pour éviter l'erreur au démarrage
RUN touch /var/lib/dhcp/dhcpd.leases


# Exposition du port DHCP standard (67/udp)
EXPOSE 67/udp

# Commande pour démarrer le serveur DHCP
ENTRYPOINT ["dhcpd", "-d", "-f", "-cf", "/etc/dhcp/dhcpd.conf", "--no-pid"]
