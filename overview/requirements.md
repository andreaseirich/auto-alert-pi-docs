# Auto-Alert-Pi - Anforderungen & Zeitplanung

## 🎯 Projektübersicht

**Projekt:** Auto-Alert-Pi - Autonomes System zur Echtzeit-Erkennung neuer Fahrzeuginserate auf willhaben.at  
**Entwickler:** Andreas Eirich  
**Projektzeitraum:** 10-14 Tage (1-2 Wochen)  
**Ziel:** Vollständige Erfassung aller neuen Inserate mit Telegram-Benachrichtigung in ≤4s  

## 📋 Funktionale Anforderungen

### Kernfunktionen
- **Vollständige Erfassung:** Alle neuen Inserate (0-50.000€) werden erkannt
- **Schnelle Reaktion:** Telegram-Benachrichtigung innerhalb von 3-4 Sekunden
- **24/7 Stabilität:** Selbstheilend, Restart-fähig, 24 Stunden Testlauf ohne Fehler
- **Nachvollziehbarkeit:** Vollständige Dokumentation aller Arbeitsschritte

### Technische Anforderungen
- **Hardware:** Raspberry Pi 4 (8GB) - aktives Entwicklungs- und Laufzeitsystem
- **Systemerweiterung:** 450-500€ (notwendig für Projektrealisierung)
- **Datenbank:** SQLite (lokal)
- **API:** willhaben.at Scraping + Telegram Bot
- **Betriebssystem:** Raspberry Pi OS

## 📅 Realistische Projektphasen

### Phase 1 – Grundlagen & Architektur (Tag 1-3)
**Ziel:** Solide Basis für die Entwicklung schaffen

**Arbeitspakete:**
- Analyse der Willhaben-Struktur und API-Verhalten
- Entwurf der Softwarearchitektur
- Einrichtung der Projektverzeichnisse und Umgebungsvariablen
- Erstellung erster Testmodule (Mock-Parser, Testdaten)
- Basis-Repository-Struktur und Git-Workflow

**Erwartete Ergebnisse:**
- Vollständige Projektstruktur
- Architektur-Dokumentation
- Erste funktionsfähige Testmodule
- Konfigurationssystem

### Phase 2 – Implementierung & Datenfluss (Tag 4-7)
**Ziel:** Kernfunktionalität implementieren

**Arbeitspakete:**
- Entwicklung der Polling-Engine für willhaben.at
- HTML-Parser und Inserat-Extraktion
- Diff-Algorithmus für neue Inserate
- Telegram-Bot Integration
- SQLite-Datenbank und API-Verbindungen
- Lokale Tests unter realistischen Bedingungen

**Erwartete Ergebnisse:**
- Funktionsfähiges Polling-System
- Erste Telegram-Benachrichtigungen
- Datenbank-Integration
- Grundlegende Fehlerbehandlung

### Phase 3 – Optimierung & Stabilisierung (Tag 8-10)
**Ziel:** System stabilisieren und optimieren

**Arbeitspakete:**
- Latenzoptimierung (3-4 Sekunden-Ziel erreichen)
- Robuste Fehlerbehandlung und Backoff-Mechanismen
- Umfassendes Logging und Monitoring
- Systemd-Service Integration
- 24-Stunden-Testlauf ohne Unterbrechungen

**Erwartete Ergebnisse:**
- Stabile Performance unter Last
- Zuverlässige Fehlerbehandlung
- Kontinuierlicher 24h-Betrieb
- Produktionsreife Konfiguration

### Phase 4 – Dokumentation & Abnahme (Tag 11-14)
**Ziel:** Projekt abschließen und übergeben

**Arbeitspakete:**
- Vollständige Entwickler-Dokumentation
- Kundendokumentation und Bedienungsanleitung
- Finale Funktionsbeschreibung
- Übergabedokumente und Testberichte
- Vorbereitung auf Kundengespräch/Review

**Erwartete Ergebnisse:**
- Vollständige Dokumentation
- Abnahmefähiges System
- Übergabepaket für den Kunden
- Abschlussbericht mit Lessons Learned

## 🧪 Test- und Abnahmebedingungen

### Zwischenstände
- **Nach Phase 1:** Funktionsfähige Projektstruktur und erste Tests
- **Nach Phase 2:** Grundfunktionalität mit ersten Benachrichtigungen
- **Nach Phase 3:** Stabiler 24h-Testlauf ohne Fehler
- **Nach Phase 4:** Vollständig dokumentiertes und abnahmefähiges System

### Abnahmekriterien
- **Funktionalität:** Alle Kernfunktionen implementiert und getestet
- **Performance:** Reaktionszeit ≤ 4 Sekunden erreicht
- **Stabilität:** 24 Stunden kontinuierlicher Betrieb ohne Fehler
- **Dokumentation:** Vollständige Entwickler- und Kundendokumentation
- **Code-Qualität:** Sauberer, dokumentierter und getesteter Code

## 📊 Fortschrittsverfolgung

### Tägliche Ziele
- Jeden Tag ein funktionsfähiger Zwischenstand
- Regelmäßige Commits und Dokumentation
- Tests der implementierten Funktionen
- Aktualisierung der Fortschrittslogs

### Qualitätssicherung
- Code-Reviews nach jeder Phase
- Umfassende Tests vor Abnahme
- Dokumentation parallel zur Entwicklung
- Kontinuierliche Integration und Deployment

## ⚠️ Risikomanagement

### Identifizierte Risiken
- **Willhaben-API-Änderungen:** Regelmäßige Anpassungen erforderlich
- **Performance-Ziele:** Optimierung kann zusätzliche Zeit benötigen
- **Stabilität:** 24h-Test kann Probleme aufdecken
- **Dokumentation:** Umfang kann unterschätzt werden

### Mitigationsstrategien
- Frühe Tests mit realen Daten
- Pufferzeit in der Planung
- Kontinuierliche Validierung
- Parallelisierung von Entwicklung und Dokumentation

---
**Letzte Aktualisierung:** 08.10.2025 17:30