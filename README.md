# VPS Ubuntu — Nginx + HTTPS (Certbot) — Portfolio BTS SIO SISR/CIEL (Alternance)

## Objectif
Mettre en production un site web sur un **VPS Ubuntu** avec **Nginx** et **HTTPS (Let’s Encrypt / Certbot)**, puis documenter une démarche “exploitation” : validation de configuration, état du service, ports en écoute, tests HTTP(S), et exemples de logs (anonymisés).

## Contexte
Projet personnel (lab) orienté **BTS CIEL** : administration d’un service web exposé sur Internet + documentation opérationnelle réutilisable (procédures et preuves).

## Compétences mobilisées
- **Linux serveur** : systemd, gestion de services, lecture de logs
- **Nginx** : vhost, redirection HTTP→HTTPS, écoute 80/443, logs
- **TLS** : Certbot / Let’s Encrypt (certificats, renouvellement)
- **Réseau** : vérification ports (ss), tests HTTP(S) (curl)
- **Sécurité & publication** : anonymisation (IP/hostname/domaines), pas de secrets dans le dépôt

---

## Architecture
Voir :
- `architecture/ports-services.md`
- `architecture/data-flow.md`

Résumé :
- Internet → **80/443** → **Nginx**
- HTTP (80) redirige vers HTTPS (443)
- HTTPS terminé par Nginx (certificats Let’s Encrypt)

---

## Configuration (anonymisée)
Fichiers de configuration à consulter :
- `configs/nginx.conf.example`
- `configs/nginx-site.conf.example`
- `configs/snippets/`

> Remarque : tous les domaines/IP/hostnames ont été remplacés (ex: `example.tld`, `XXX.XXX.XXX.XXX`).

---

## Preuves / tests (anonymisés)
### Validation & état du service
- `proofs/1_nginx_test.txt` : validation de la configuration (`nginx -t`)
- `proofs/2_nginx_status.txt` : état du service (`systemctl status nginx`)
- `proofs/3_ports_80_443.txt` : ports en écoute (80/443)

### Certificats & tests HTTP(S)
- `proofs/5_certbot_certificates.txt` : certificats actifs (Certbot)
- `proofs/7_curl_https.txt` : en-têtes HTTPS (réponse)
- `proofs/8_curl_http.txt` : redirection HTTP → HTTPS

### Logs (exemples anonymisés)
- `proofs/9_nginx_error_tail.txt` : extrait error log
- `proofs/10_nginx_access_tail.txt` : extrait access log

---

## Captures d’écran (anonymisées)
- `screenshots/s1_nginx_version.png` : version Nginx
- `screenshots/s2_ports_80_443.png` : ports 80/443 en écoute
- `screenshots/s3_systemctl_nginx_status.png` : service actif
- `screenshots/s4_curl_https_headers.png` : en-têtes HTTPS

---

## Procédures (runbook)
- `procedures/deploy.md` : déployer/mettre à jour le site
- `procedures/renew-ssl.md` : renouvellement Certbot
- `procedures/troubleshooting.md` : dépannage (Nginx / TLS / ports / logs)

---

## Points d’attention (améliorations identifiées)
Lors de `nginx -t`, des **warnings** peuvent apparaître (ex: conflits `server_name` / OCSP stapling) : la config reste valide, mais ces points sont à corriger pour une configuration encore plus propre (nettoyage des vhosts, vérification stapling/chain).

---

## Sécurité / confidentialité
- IP, domaines et hostnames **masqués**
- Aucun secret versionné (clés privées, tokens, `.env`)
- Logs publiés : **anonymisés** (pas d’IP client réelle, pas d’identifiants)

