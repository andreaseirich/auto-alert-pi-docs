# Auto-Alert-Pi - Systemarchitektur

## 🏗️ Übersicht

Das Auto-Alert-Pi System ist ein asynchrones, hochperformantes System zur Echtzeit-Erkennung neuer Fahrzeuginserate auf willhaben.at mit automatischer Telegram-Benachrichtigung.

## 🎯 Kernziele
- **Reaktionszeit:** ≤ 4 Sekunden
- **Vollständigkeit:** 100% aller neuen Inserate
- **Verfügbarkeit:** 24/7 Betrieb
- **Skalierbarkeit:** Raspberry Pi 4 mit optionaler Systemerweiterung

## 🔧 Systemkomponenten

### 1. Polling Engine
- **Technologie:** asyncio + aiohttp
- **Funktion:** Kontinuierliches Abfragen der willhaben.at API
- **Intervall:** 1-2 Sekunden
- **Rate Limiting:** Intelligente Anpassung basierend auf Server-Response

### 2. Parser & Filter
- **Technologie:** BeautifulSoup4 + lxml
- **Funktion:** HTML-Parsing und Inserat-Extraktion
- **Filter:** Preisbereich (0-50.000€), Fahrzeugtyp, etc.
- **Deduplizierung:** Hash-basierte Erkennung bereits bekannter Inserate

### 3. Database Layer
- **Technologie:** SQLite + SQLAlchemy
- **Funktion:** Lokale Speicherung aller Inserate
- **Schema:** Inserate, Benachrichtigungen, Systemlogs
- **Backup:** Automatische Sicherung

### 4. Notification System
- **Technologie:** python-telegram-bot
- **Funktion:** Sofortige Benachrichtigung bei neuen Inseraten
- **Format:** Strukturierte Nachrichten mit Bildern und Details
- **Retry-Logic:** Automatische Wiederholung bei Fehlern

### 5. Monitoring & Health
- **Technologie:** Custom Health Checks
- **Funktion:** Systemüberwachung und Selbstheilung
- **Logging:** Strukturiertes Logging mit Rotation
- **Restart:** Automatischer Neustart bei Fehlern

## 📊 Datenfluss

```
willhaben.at API → Polling Engine → Parser → Filter → Database
                                                      ↓
Telegram Bot ← Notification System ← New Inserate Detection
```

## 🔄 Architektur-Prinzipien

### Asynchrone Verarbeitung
- Alle I/O-Operationen asynchron
- Non-blocking Database-Operationen
- Parallele API-Requests

### Fehlerbehandlung
- Graceful Degradation
- Automatische Retry-Mechanismen
- Circuit Breaker Pattern

### Performance-Optimierung
- Connection Pooling
- Caching häufig abgerufener Daten
- Batch-Processing für Database-Operationen

## 🛠️ Technologie-Stack

### Core
- **Python 3.11+**
- **asyncio** - Asynchrone Programmierung
- **aiohttp** - HTTP Client/Server
- **SQLAlchemy** - ORM
- **SQLite** - Datenbank

### Parsing & Processing
- **BeautifulSoup4** - HTML-Parsing
- **lxml** - XML/HTML Parser
- **hashlib** - Deduplizierung

### Notifications
- **python-telegram-bot** - Telegram API
- **Pillow** - Bildverarbeitung

### Monitoring & Logging
- **structlog** - Strukturiertes Logging
- **psutil** - System-Monitoring
- **schedule** - Task-Scheduling

## 📁 Code-Struktur

```
src/
├── core/
│   ├── poller.py          # Haupt-Polling-Engine
│   ├── parser.py          # HTML-Parser
│   └── filter.py          # Inserat-Filter
├── database/
│   ├── models.py          # SQLAlchemy Models
│   ├── connection.py      # DB-Verbindung
│   └── migrations/        # Schema-Updates
├── notifications/
│   ├── telegram_bot.py    # Telegram-Integration
│   └── formatter.py       # Nachrichten-Formatierung
├── monitoring/
│   ├── health_check.py    # System-Health
│   └── logger.py          # Logging-System
└── config/
    ├── settings.py        # Konfiguration
    └── constants.py       # Konstanten
```

## 🚀 Deployment-Strategie

### Entwicklung und Betrieb (Raspberry Pi 4)
- Lokale Entwicklung und Tests
- Produktiver Betrieb des Systems
- SQLite-Datenbank
- Direkte API-Zugriffe

### Systemerweiterung (Optional)
- Zusätzliche Hardware zur Infrastruktur-Erweiterung
- Erhöhte Ausfallsicherheit und Redundanz
- Kapazitätserweiterung für zukünftige Projekte

## 📈 Performance-Ziele

| Metrik | Ziel | Messung |
|--------|------|---------|
| Reaktionszeit | ≤ 4s | API-Request bis Telegram |
| CPU-Nutzung | < 30% | Durchschnittliche Last |
| RAM-Verbrauch | < 2GB | Peak-Verbrauch |
| DB-Performance | < 100ms | Query-Response-Zeit |
| Verfügbarkeit | 99.9% | Uptime pro Monat |

---
**Letzte Aktualisierung:** 08.10.2025 15:15