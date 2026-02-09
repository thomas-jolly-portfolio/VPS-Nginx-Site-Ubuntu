# Déploiement (site Nginx)

## Objectif
Mettre à jour le contenu du site sans casser la config Nginx.

## Étapes
1. Copier les fichiers du site dans `/var/www/site` (exemple).
2. Vérifier droits : `www-data` (ou utilisateur du service).
3. Valider Nginx : `sudo nginx -t`
4. Reload : `sudo systemctl reload nginx`

## Vérifications
- `curl -I https://example.tld`
- contrôle des logs Nginx si besoin

