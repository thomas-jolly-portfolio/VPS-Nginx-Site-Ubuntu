# Dépannage Nginx

## Valider la configuration
sudo nginx -t

## Recharger / Redémarrer
sudo systemctl reload nginx
sudo systemctl restart nginx

## Voir l’état
systemctl status nginx --no-pager

## Vérifier écoute ports
sudo ss -tulpn | grep -E ':80|:443|nginx'

## Logs
sudo tail -n 80 /var/log/nginx/error.log
sudo tail -n 80 /var/log/nginx/access.log

## Test HTTP(S)
curl -I https://example.tld
curl -I http://example.tld

