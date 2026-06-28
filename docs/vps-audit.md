# Read-only VPS audit

Diese Prüfung erfolgt vor jeder Installation. Die Befehle verändern das System nicht.

## 1. Betriebssystem und Host

```bash
hostnamectl
cat /etc/os-release
uname -a
```

## 2. Ressourcen

```bash
free -h
df -h
nproc
```

## 3. Laufende Dienste

```bash
systemctl --type=service --state=running --no-pager
systemctl --type=service --state=running --no-pager | grep -Ei 'docker|nginx|apache|caddy|traefik|mysql|mariadb|postgres|redis|node|pm2'
```

## 4. Docker

```bash
docker --version
docker compose version
docker ps --format "table {{.Names}}\t{{.Image}}\t{{.Ports}}\t{{.Status}}"
docker network ls
docker volume ls
```

## 5. Belegte Ports

```bash
sudo ss -tulpn
```

## 6. Reverse Proxy

```bash
which nginx
which apache2
which caddy
which traefik
sudo nginx -T 2>/dev/null | head -n 120
```

## 7. Projektverzeichnisse

```bash
ls -la /opt
ls -la /srv
ls -la /var/www
ls -la /home
```

## 8. Compose-Dateien finden

```bash
sudo find /opt /srv /home /var/www -maxdepth 4 \
  \( -name "docker-compose.yml" -o -name "docker-compose.yaml" -o -name "compose.yml" -o -name "compose.yaml" \) \
  2>/dev/null
```

## 9. Domains und Zertifikate

```bash
sudo ls -la /etc/letsencrypt/live 2>/dev/null
sudo grep -R "server_name" /etc/nginx/sites-enabled /etc/nginx/conf.d 2>/dev/null
```

## Datenschutz

Vor dem Teilen der Ausgabe entfernen:

- Passwörter und Tokens
- Inhalte von `.env`-Dateien
- private Schlüssel
- Zugangsdaten in URLs
- personenbezogene Daten

Öffentliche IP-Adressen und interne Hostnamen sollten in einem öffentlichen Issue nicht gepostet werden. Die Audit-Ausgabe wird nur lokal beziehungsweise im privaten Chat ausgewertet.
