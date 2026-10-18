# GitHub / VPS: zentraler Betriebspfad

Auftrag #1. Dieses **öffentliche** Repository plant TradingView-Alarmverarbeitung mit n8n, Airtable und Telegram ausschließlich für Paper-Trading. Vor Installation oder Änderung an einem bereits genutzten Netcup-VPS ist dessen aktueller Zustand lesend und konfliktfrei zu erfassen.

## Zugang getrennt von diesem Repository

- [Privates zentrales Operations-Repository](https://github.com/Cillyonline/cillyonline-core)
- [Zentraler VPS-GitHub-Actions-Lesetest](https://github.com/Cillyonline/cillyonline-core/actions/workflows/vps-readonly.yml)
- [Einmalige Einrichtung des Nicht-Root-SSH-Schlüssels](https://github.com/Cillyonline/cillyonline-core/blob/main/docs/VPS_READONLY.md)
- [Projekt-Routing und Freigabegrenzen](https://github.com/Cillyonline/cillyonline-core/blob/main/docs/VPS_PROJECT_ROUTING.md)
- [Vorhandener Sicherheits-/Inventurentwurf](vps-audit.md)

Der zentrale Workflow prüft nur `whoami`, **nicht** die Container, Dienste, Ports, n8n-Konfiguration oder Erreichbarkeit der Anwendung. SSH-Benutzer, verifizierter VPS-Hostkey und Secret müssen zentral noch eingerichtet und der reale Actions-Lauf bestätigt werden.

## Grenzen

- Keine SSH-Schlüssel/Secrets, Server-IP, interne Hostnamen, n8n-Tokens oder produktiven Webhook-Geheimnisse in diesem öffentlichen Repository hinterlegen.
- Keine Root- oder Docker-Gruppenberechtigung für den nur lesenden VPS-Prüfbenutzer.
- Keine `workflow_call`-Brücke von einem öffentlichen Repo zu einem privaten Core-Workflow. Keine GitHub-Tokens in Repository-Issues oder Dateien.
- Keine automatische Installation, Veröffentlichung, Trading-Ausführung oder Änderung an vorhandenen Docker-Containern, Caddy/Reverse-Proxy, Firewall, Ports und Volumes.
- Für konkrete n8n-Inventur, Staging oder späteres Deployment erst aktuellen VPS-Bestand, getrennte Datenhaltung, Sicherung und Rückwechsel überprüfen und einen neuen eng gefassten Betreiberauftrag freigeben.

Der Text konfiguriert lediglich den **zentralen Zugriffsweg** und fügt diesem Repository bewusst keinen VPS-Actions-Job hinzu. Rückwechsel: Dokument revertieren.
