# Ports & services — VPS Ubuntu

## Ports exposés
- 22/tcp : SSH (administration)
- 80/tcp : HTTP (redirection vers HTTPS)
- 443/tcp : HTTPS (site web)

## Services
- nginx : serveur web / reverse proxy
- certbot : gestion certificats TLS Let's Encrypt
- systemd : gestion des services
- logs : /var/log/nginx/access.log, /var/log/nginx/error.log

