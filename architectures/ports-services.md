# Ports & services — VPS Ubuntu (Nginx + HTTPS)

## Ports exposés (Internet → VPS)
- 22/tcp : SSH (administration)
- 80/tcp : HTTP (redirection vers HTTPS)
- 443/tcp : HTTPS (site web)

## Services
- nginx : serveur web / reverse proxy
- certbot : gestion certificats TLS (Let’s Encrypt)
- (optionnel) php-fpm : exécution PHP côté serveur
- ufw : pare-feu
- fail2ban : protection brute-force (projet séparé si tu le fais)

## Logs
- /var/log/nginx/access.log
- /var/log/nginx/error.log
- (optionnel) logs par vhost : /var/log/nginx/example.access.log / example.error.log

## Points de contrôle (exploitation)
- Validation config : `nginx -t`
- État service : `systemctl status nginx`
- Écoute ports : `ss -tulpn | grep -E ':80|:443'`
- Test HTTP(S) : `curl -sI https://example.tld`

