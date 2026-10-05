# Sensor-Baukasten – W-Seminar

Web-App aus dem W-Seminar „Steuerung von Mikroprozessoren“.
Sie zeigt alle Sensoren mit 3D-Modell, Verkabelung, technischen Daten und Quellcode,
übernimmt phyphox-Exporte, speichert Messungen auf dem Gerät und exportiert sie
als Text oder Excel-Datei (.xlsx, öffnet auch in LibreOffice).
Als installierbare App (PWA) läuft sie auch offline.

## Dateien

| Datei | Zweck |
| --- | --- |
| `index.html` | die App selbst |
| `manifest.webmanifest` | Name, Icon und Farben für die Installation |
| `sw.js` | Service Worker, macht die App offline nutzbar |
| `three.min.js` | 3D-Bibliothek three.js r128 (MIT-Lizenz) |
| `xlsx.full.min.js` | SheetJS 0.18.5 für den Excel-Export (Apache-2.0-Lizenz) |
| `icons/` | App-Icons für iPhone, iPad, Android und PC |
| `.nojekyll` | sorgt dafür, dass GitHub Pages alle Dateien unverändert ausliefert |

## Online stellen mit GitHub Pages

1. Auf github.com ein kostenloses Konto anlegen.
2. Neues Repository anlegen, z. B. `sensor-baukasten`, Sichtbarkeit **Public**.
3. „Add file“ → „Upload files“ und den **Inhalt** dieses Ordners hochladen
   (alle Dateien und den Ordner `icons`, nicht den äußeren Ordner selbst).
4. „Settings“ → „Pages“: Quelle „Deploy from a branch“, Branch `main`, Ordner `/ (root)`, speichern.
5. Nach ein bis zwei Minuten ist die App erreichbar unter
   `https://BENUTZERNAME.github.io/sensor-baukasten/`

## Installieren

- **iPhone / iPad:** Adresse in Safari öffnen → Teilen → „Zum Home-Bildschirm“.
- **PC / Mac:** Adresse in Chrome oder Edge öffnen → Installieren-Symbol in der Adressleiste
  oder Knopf „App installieren“ in der App.
- **Android:** Adresse in Chrome öffnen → „App installieren“.

Nach dem ersten Öffnen mit Internet funktioniert die App auch ohne Verbindung.

## Messen direkt im Browser (ohne phyphox-App)

Unter „Messen“ → „Direkt im Browser“ verbindet sich die App per Web Bluetooth mit dem ESP32.
Der ESP32 braucht dafür dasselbe Programm wie für phyphox (Bibliothek „phyphox BLE“).

- Funktioniert in **Chrome** und **Edge** auf Windows, Mac, Android und ChromeOS.
- **iPhone / iPad:** Safari unterstützt kein Web Bluetooth. Die Adresse in der kostenlosen
  App „Bluefy – Web BLE Browser“ öffnen oder den Weg „Mit phyphox-App“ nutzen.
- Firefox unterstützt kein Web Bluetooth.
- Ein ESP32 kann nur mit einem Gerät gleichzeitig verbunden sein.

## Updates

Neue Dateien hochladen und in `sw.js` die Zeile `const VERSION = "sensor-baukasten-v3";`
hochzählen (`v4`, `v5`, …). Die installierten Apps laden die neue Fassung beim nächsten Start
mit Internet; spätestens nach zweimaligem Öffnen ist sie aktiv.

## Hinweise

- Messungen und geladene Gehäuse werden im Speicher des jeweiligen Geräts abgelegt.
  Auf dem iPhone sind die Daten der installierten App getrennt von Safari.
  Wichtige Messungen deshalb als Text herunterladen.
- Lokales Testen: Ein Doppelklick auf `index.html` funktioniert, aber ohne Offline-Modus.
  Der Service Worker braucht eine http(s)-Adresse.
