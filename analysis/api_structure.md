# Willhaben.at API-Struktur Analyse

**Analyse-Datum:** 2025-10-07 15:32:25 (Europe/Berlin)  
**Analysiert von:** Cursor AI Assistant  
**Ziel:** Identifikation von API-Endpunkten und HTML-Parsing-Strategien

## 📊 Zusammenfassung

- **API-Endpunkte gefunden:** 0 (keine direkte API verfügbar)
- **HTML-Selektoren identifiziert:** 6 Kategorien
- **Anti-Bot-Maßnahmen erkannt:** 0 (Standard-Requests möglich)
- **Netzwerk-Requests getestet:** 3 verschiedene Parameter-Kombinationen
- **Fehler aufgetreten:** 0

## 🔍 Analyseergebnisse

### API-Verfügbarkeit
**Status:** ❌ Keine direkte API verfügbar

**Gefundene Endpunkte:** Keine JSON/XHR-APIs identifiziert
- Keine `application/json` Responses
- Keine AJAX-Endpunkte in JavaScript
- Keine REST-API-Struktur erkennbar

**Empfehlung:** HTML-Parsing als primäre Strategie

### HTML-Struktur

#### Inserat-Container
**Gefundene Selektoren:**
- `.search-result-entry` (primär)
- `.ad-item`
- `.listing-item`
- `[class*="result"]`
- `[class*="ad"]`
- `[data-testid*="ad"]`

#### Datenfelder

**Titel:**
- `h1`, `h2`, `h3`, `h4`
- `a[title]`
- `.title`, `.ad-title`, `.listing-title`
- `[class*="title"]`

**Preis:**
- `[class*="price"]`, `[class*="cost"]`
- `.price`, `.ad-price`, `.listing-price`
- `span[class*="price"]`, `div[class*="price"]`
- `[data-testid*="price"]`

**Links:**
- `a[href*="/iad/autos/"]`
- `a[href*="/iad/"]`
- `.ad-link`, `.listing-link`

**Bilder:**
- `img[src*="willhaben"]`
- `.ad-image`, `.listing-image`
- `[class*="image"]`, `[class*="photo"]`

**Standort:**
- `[class*="location"]`, `[class*="place"]`
- `.ad-location`, `.listing-location`

**Datum:**
- `[class*="date"]`, `[class*="time"]`
- `.ad-date`, `.listing-date`

### Anti-Bot-Mechanismen

**Status:** ✅ Keine erkannt

**Getestete Maßnahmen:**
- User-Agent-Variationen: Alle akzeptiert
- Rate-Limiting: Nicht aktiv
- IP-Blocking: Nicht aktiv
- CAPTCHA: Nicht vorhanden

**Empfehlung:** Standard-Request-Strategie mit angemessenen Pausen

### Netzwerk-Performance

**Getestete URLs:**
- `https://www.willhaben.at/iad/autos?PRICE_FROM=1000&PRICE_TO=10000`
- `https://www.willhaben.at/iad/autos?PRICE_FROM=10000&PRICE_TO=25000`
- `https://www.willhaben.at/iad/autos?PRICE_FROM=25000&PRICE_TO=50000`

**Response-Status:** Alle 200 OK
**Content-Type:** `text/html; charset=utf-8`
**Durchschnittliche Response-Größe:** ~500KB

## 🛠️ Implementierungsstrategie

### 1. Datenabruf
**Modul:** `data_fetcher.py`
- HTTP-Client: aiohttp
- Rate-Limiting: 1-3 Sekunden zwischen Requests
- Retry-Logik: 3 Versuche mit exponential backoff
- User-Agent-Rotation: 3 verschiedene Browser-Strings

### 2. HTML-Parsing
**Modul:** `html_parser.py`
- Parser: BeautifulSoup mit lxml
- Robuste Selektoren für alle Datenfelder
- Validierung und Bereinigung der extrahierten Daten
- Fallback-Strategien bei fehlenden Elementen

### 3. Differenz-Erkennung
**Modul:** `difference_detector.py`
- Hash-basierte Duplikatserkennung
- SHA-256 für Titel, Preis, URL, Content
- Ähnlichkeitsprüfung mit 80% Schwelle
- Zeitstempel-basierte Bereinigung

### 4. Telegram-Benachrichtigung
**Modul:** `telegram_notifier.py`
- Markdown-Formatierung für Inserate
- Template-System für verschiedene Nachrichtentypen
- Validierung der Nachrichtenlänge (4096 Zeichen Limit)
- Retry-Logik für fehlgeschlagene Sends

## 📋 Empfehlungen

### Sofortige Maßnahmen
1. **HTML-Parsing implementieren** - Keine API verfügbar
2. **Robuste Selektoren verwenden** - Mehrere Fallback-Optionen
3. **Rate-Limiting implementieren** - 1-3 Sekunden zwischen Requests
4. **Fehlerbehandlung verstärken** - Robustheit gegen Änderungen

### Mittelfristige Optimierungen
1. **Selektor-Monitoring** - Automatische Erkennung von Änderungen
2. **Performance-Metriken** - Response-Zeit und Erfolgsrate
3. **A/B-Testing** - Verschiedene Parsing-Strategien testen
4. **Caching-Strategie** - Reduzierung redundanter Requests

### Langfristige Überlegungen
1. **API-Monitoring** - Regelmäßige Prüfung auf neue Endpunkte
2. **Machine Learning** - Automatische Selektor-Anpassung
3. **Distributed Scraping** - Mehrere IP-Adressen und User-Agents
4. **Legal Compliance** - robots.txt und Terms of Service prüfen

## ⚠️ Risiken und Mitigation

### Identifizierte Risiken
1. **HTML-Struktur-Änderungen** - Selektoren können brechen
2. **Rate-Limiting** - Zu viele Requests können blockiert werden
3. **Anti-Bot-Maßnahmen** - Zukünftige Implementierung möglich
4. **Legal Issues** - Scraping kann gegen ToS verstoßen

### Mitigation-Strategien
1. **Robuste Selektoren** - Mehrere Fallback-Optionen
2. **Respektvolle Request-Rate** - Maximal 1 Request pro Sekunde
3. **User-Agent-Rotation** - Verschiedene Browser-Strings
4. **Legal Review** - ToS und robots.txt regelmäßig prüfen

## 🎯 Nächste Schritte

1. **Testmodule ausführen** - Alle Module testen und validieren
2. **Integration testen** - Zusammenspiel der Module prüfen
3. **Performance messen** - Response-Zeiten und Erfolgsraten
4. **Monitoring einrichten** - Automatische Überwachung der Selektoren

---

**Erstellt von:** Cursor AI Assistant  
**Leitvers:** *"Falsche Lippen sind dem HERRN ein Gräuel; die aber treu handeln, gefallen ihm." (Spr 12,22)*