# tradingview-bot

TradingView alert automation for a mobile-friendly paper-trading workflow.

## Ziel

Das Projekt verbindet schrittweise:

- TradingView-Alarme
- n8n auf einem bestehenden VPS
- Airtable als Watchlist-, Alarm- und Paper-Trade-Datenbank
- Telegram für mobile Benachrichtigungen
- ChatGPT für Chart- und Triggerprüfungen

## Geplanter Ablauf

```text
TradingView
    ↓ Webhook
n8n
    ↓
Airtable
    ↓
Telegram
    ↓
manuelle Triggerprüfung in ChatGPT
```

## Projektstatus

Das Repository befindet sich im Aufbau. Vor der n8n-Installation wird der bestehende VPS ausschließlich lesend analysiert, damit vorhandene Projekte, Reverse Proxies, Docker-Netzwerke und Ports nicht beeinträchtigt werden.

## Sicherheit

Dieses Repository ist öffentlich. Folgende Daten dürfen niemals committed werden:

- `.env`
- API-Token und Passwörter
- Airtable- und Telegram-Zugangsdaten
- n8n-Verschlüsselungsschlüssel
- SSH-Schlüssel
- vollständige n8n-Credential-Backups
- produktive Webhook-Geheimnisse

Nur `.env.example` mit Platzhaltern wird versioniert.

## Nächste Schritte

1. Bestehenden VPS und laufende Dienste analysieren.
2. Deployment-Struktur an die vorhandenen Projekte anpassen.
3. n8n mit persistenter Datenhaltung und HTTPS bereitstellen.
4. TradingView-Webhook empfangen und validieren.
5. Airtable-Datensätze aktualisieren.
6. Telegram-Benachrichtigungen ergänzen.
