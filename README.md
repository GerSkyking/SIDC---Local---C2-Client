# SIDC - Local - C2 Client

Verteil-Repo für die fertig gebaute Windows-Client-Version von **ATAKmaps / SIDC-C2**
(kein Python nötig). Der Quellcode liegt im Hauptprojekt (`ATAKmaps`); dieses Repo
enthält nur Release-Infos und Anleitungen — die eigentliche Anwendung wird als ZIP an
die [Releases](../../releases) dieses Repos angehängt.

## Installation

1. Aktuellstes Release herunterladen (ZIP unter [Releases](../../releases)) und entpacken.
2. **`3 - Setup starten.bat`**
   * Reiter **SIDC-Profile**: `SIDC_Framework`-Ordner der Reforger-Installation wählen
     (enthält `LocalMapData`).
   * Reiter **Karten & DLC**: mindestens ein Kartenpaket (.zip) importieren.
   * Reiter **Kartenserver** (optional): Adresse + Token eines SIDC-C2-Kartenservers
     eintragen, um Basiskarten ohne lokalen Import zu laden.
3. **`1 - Web Server starten.bat`** (Fenster offen lassen)
4. **`2 - Browser starten.bat`** (öffnet `http://localhost:8765`)

Es muss kein Python installiert sein — beides sind eigenständige EXEs.

## Neues Release bauen

Der Build passiert im Hauptprojekt-Repo `ATAKmaps`:

```
cd web && npm run build     # Web-Frontend
cd ..  && python build_client.py
```

Ergebnis landet unter `D:/Mods/ATAKmapsClient/win/`. Diesen Ordner zippen und als
neues [Release](../../releases/new) hier hochladen.

## Was ist neu in dieser Version

* Optionaler **Kartenserver** (SIDC-C2): Basiskarten können jetzt von einem Server
  geladen werden, statt nur aus lokal importierten Kartenpaketen. Lokale Karten haben
  weiterhin Vorrang, der Server füllt nur auf, was lokal fehlt. Marker, Live-Position
  und Kalibrierung bleiben immer lokal.
* Verwaltung von Kartenserver-Zugang direkt im Setup-Tool (Reiter „Kartenserver").
