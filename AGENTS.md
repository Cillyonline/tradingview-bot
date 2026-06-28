# AGENTS.md

## Projektziel

Dieses Repository automatisiert TradingView-Alarme über n8n und verbindet sie mit Airtable und Telegram. Der Prozess dient zunächst ausschließlich dem Paper-Trading.

## Arbeitsregeln

- Keine produktiven Secrets, Tokens, Passwörter oder privaten Schlüssel committen.
- Vor Änderungen an Deployment-Dateien zuerst die bestehende VPS-Struktur prüfen.
- Bestehende Dienste, Ports, Docker-Netzwerke und Reverse-Proxy-Konfigurationen nicht ohne dokumentierte Analyse verändern.
- Infrastrukturänderungen klein, nachvollziehbar und reversibel halten.
- `.env.example` enthält ausschließlich Platzhalter.
- n8n-Workflows nur ohne eingebettete Credentials exportieren.
- TradingView-Alarme lösen niemals automatisch einen echten Trade aus.
- Ein Alarm setzt einen Kandidaten zunächst nur auf `TRIGGERED`; die Freigabe erfolgt erst nach erneuter Prüfung.

## Geplante Verzeichnisse

- `docs/` – Architektur, Betrieb und Runbooks
- `n8n/workflows/` – bereinigte Workflow-Exporte
- `scripts/` – Hilfs- und Prüfscripte
- `config/` – versionsfähige Konfigurationsvorlagen
- `.github/workflows/` – CI-Prüfungen

## Qualitätsanforderungen

- Shell-Skripte mit `set -euo pipefail`.
- YAML und JSON müssen syntaktisch validierbar sein.
- Änderungen an Webhook-Payloads dokumentieren.
- Fehlerpfade, doppelte Alarme und ungültige Secrets berücksichtigen.
- Öffentliche Dokumentation darf keine internen Hostnamen, IP-Adressen oder Zugangsdaten offenlegen.
