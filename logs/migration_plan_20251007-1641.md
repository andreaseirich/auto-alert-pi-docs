# Migrationsplan - Strukturkonsolidierung

**Erstellt:** 2025-10-07 16:41:02 (Europe/Berlin)  
**Ziel:** Alle Repositories ausschließlich unter `~/projects/` konsolidieren

## 📊 Inventur-Ergebnisse

### 🔍 Gefundene Verzeichnisse

| **Verzeichnis** | **Typ** | **Git-Status** | **Letzter Commit** | **Bewertung** |
|-----------------|---------|----------------|-------------------|----------------|
| `~/auto-alert-pi` | Verzeichnis | Kein Git-Repo | - | **Leer/Alt** |
| `~/auto-alert-pi-docs` | Verzeichnis | Kein Git-Repo | - | **Leer/Alt** |
| `~/auto-alert-pi-client-doc` | Verzeichnis | Kein Git-Repo | - | **Leer/Alt** |
| `~/projects/auto-alert-pi` | Git-Repo | ✅ Aktiv | 0078581 | **KANONISCH** |
| `~/projects/auto-alert-pi-docs` | Git-Repo | ✅ Aktiv | ecdeb30 | **KANONISCH** |
| `~/projects/auto-alert-pi-client-doc` | Git-Repo | ✅ Aktiv | 5e5710d | **KANONISCH** |

### 📋 Duplikat-Analyse

**Ergebnis:** Keine echten Duplikate gefunden
- Home-Verzeichnisse enthalten **keine Git-Repositories**
- Home-Verzeichnisse sind **leer oder enthalten nur minimale Inhalte**
- Alle aktiven Repositories befinden sich bereits in `~/projects/`

### 🎯 Migrationsstrategie

**Strategie:** **Sichere Bereinigung** (keine Migration erforderlich)

1. **Backup erstellen** - Home-Verzeichnisse als `.OLD-<timestamp>` sichern
2. **Inhalte prüfen** - Sicherstellen, dass keine wichtigen Dateien verloren gehen
3. **Verzeichnisse umbenennen** - Home-Verzeichnisse als Backup markieren
4. **Pfade prüfen** - Sicherstellen, dass alle Referenzen auf `~/projects/` zeigen

## 🔄 Detaillierter Migrationsplan

### Phase 1: Backup & Sicherung
```bash
# Backup-Tags in allen aktiven Repos
cd ~/projects/auto-alert-pi && git tag backup-pre-structure-fix-20251007-1641
cd ~/projects/auto-alert-pi-docs && git tag backup-pre-structure-fix-20251007-1641
cd ~/projects/auto-alert-pi-client-doc && git tag backup-pre-structure-fix-20251007-1641

# Safety-Backup der Home-Verzeichnisse
mkdir -p ~/projects/_safety_backups
cp -r ~/auto-alert-pi ~/projects/_safety_backups/auto-alert-pi/20251007-1641/ 2>/dev/null || true
cp -r ~/auto-alert-pi-docs ~/projects/_safety_backups/auto-alert-pi-docs/20251007-1641/ 2>/dev/null || true
cp -r ~/auto-alert-pi-client-doc ~/projects/_safety_backups/auto-alert-pi-client-doc/20251007-1641/ 2>/dev/null || true
```

### Phase 2: Inhaltsprüfung
```bash
# Prüfe, ob Home-Verzeichnisse wichtige Inhalte enthalten
find ~/auto-alert-pi -type f -name "*.md" -o -name "*.py" -o -name "*.json" -o -name "*.yml" 2>/dev/null
find ~/auto-alert-pi-docs -type f -name "*.md" -o -name "*.py" -o -name "*.json" -o -name "*.yml" 2>/dev/null
find ~/auto-alert-pi-client-doc -type f -name "*.md" -o -name "*.py" -o -name "*.json" -o -name "*.yml" 2>/dev/null
```

### Phase 3: Umbenennung (Backup)
```bash
# Home-Verzeichnisse als Backup markieren
mv ~/auto-alert-pi ~/auto-alert-pi.OLD-20251007-1641 2>/dev/null || true
mv ~/auto-alert-pi-docs ~/auto-alert-pi-docs.OLD-20251007-1641 2>/dev/null || true
mv ~/auto-alert-pi-client-doc ~/auto-alert-pi-client-doc.OLD-20251007-1641 2>/dev/null || true
```

### Phase 4: Pfad-Korrekturen
```bash
# Suche nach Pfad-Referenzen in allen Repos
grep -r "~/auto-alert-pi" ~/projects/auto-alert-pi/ 2>/dev/null || true
grep -r "~/auto-alert-pi-docs" ~/projects/auto-alert-pi-docs/ 2>/dev/null || true
grep -r "~/auto-alert-pi-client-doc" ~/projects/auto-alert-pi-client-doc/ 2>/dev/null || true
```

## ⚠️ Risikobewertung

### 🟢 Niedriges Risiko
- Keine aktiven Git-Repositories im Home-Verzeichnis
- Alle wichtigen Daten bereits in `~/projects/` gesichert
- Keine Datenverluste zu erwarten

### 🟡 Mittleres Risiko
- Mögliche versteckte Konfigurationsdateien
- Systemd-Services oder Cron-Jobs könnten alte Pfade referenzieren

### 🔴 Maßnahmen
- Vollständige Backup-Strategie implementiert
- Schrittweise Umbenennung statt sofortiges Löschen
- Verifikation nach jedem Schritt

## 📋 Verifikations-Checkliste

- [ ] Backup-Tags in allen Repos erstellt
- [ ] Safety-Backup der Home-Verzeichnisse erstellt
- [ ] Inhaltsprüfung der Home-Verzeichnisse durchgeführt
- [ ] Home-Verzeichnisse als `.OLD-<timestamp>` umbenannt
- [ ] Pfad-Referenzen in allen Repos geprüft und korrigiert
- [ ] Git-Integrität aller Repos verifiziert
- [ ] Alle Repos gepusht und synchronisiert

## 🎯 Erwartetes Ergebnis

**Nach der Migration:**
- Alle Repositories ausschließlich unter `~/projects/`
- Keine Duplikate oder verwaiste Verzeichnisse
- Alle Pfad-Referenzen korrekt auf `~/projects/` gerichtet
- Home-Verzeichnisse als `.OLD-<timestamp>` gesichert
- Vollständige Git-Historie erhalten

---

**Migrationsplan erstellt von:** Cursor AI Assistant  
**Prüfungsstandard:** Sprüche 12,22 - Wahrhaftigkeit und Verantwortlichkeit  
**Plan erstellt:** 2025-10-07 16:41:02 (Europe/Berlin)