# Renouvellement HTTPS (Certbot)

## Vérifier les certificats
sudo certbot certificates

## Tester le renouvellement (recommandé)
sudo certbot renew --dry-run

## Renouvellement réel
sudo certbot renew

## Vérifier timer / automatisation
systemctl list-timers | grep -i certbot

## Logs utiles
sudo journalctl -u nginx --no-pager

