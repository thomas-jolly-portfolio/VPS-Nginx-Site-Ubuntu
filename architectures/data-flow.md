# Flux de données (Data flow)

## Requête HTTPS
1. Le client (navigateur) contacte `https://example.tld` sur le port **443**
2. Nginx termine le chiffrement TLS (certificat Let’s Encrypt)
3. Nginx sert :
   - soit des fichiers statiques depuis `/var/www/site`
   - soit transmet au backend (ex: PHP-FPM) pour les pages dynamiques
4. Nginx renvoie la réponse HTTP au client

## Redirection HTTP → HTTPS
1. Le client contacte `http://example.tld` sur le port **80**
2. Nginx répond `301` vers `https://example.tld/...`

## Composants impliqués
- DNS (résolution du domaine vers l’IP du VPS) *(domaine masqué dans le portfolio)*
- Nginx (reverse proxy / serveur web)
- (optionnel) PHP-FPM (traitement PHP)
- Système de logs (traces d’accès et erreurs)

