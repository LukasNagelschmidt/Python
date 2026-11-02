# phyphox Terminal

Ein Terminal im Browser, mit dem du Python-Skripte direkt auf deinen phyphox-Messdaten (ZIP-Dateien) ausführen kannst, ohne Python zu installieren.

Alles läuft lokal in deinem Browser. Deine Dateien werden nirgendwo hochgeladen.

## So funktioniert es

1. Öffne `index.html` im Browser.
2. Ziehe deine Python-Datei (z. B. `flip_detector.py`) in das Fenster. Vorher ist das Terminal gesperrt.
3. Ziehe deine phyphox-ZIP-Dateien in die Seitenleiste (oder irgendwo ins Fenster). Du kannst jederzeit weitere hinzufügen oder einzelne mit ✕ entfernen.
4. Der Befehl ist schon vorgeschrieben, z. B.:
   ```
   python3 flip_detector.py *.zip
   ```
   Mit Enter ausführen. `*.zip` steht für alle hinzugefügten ZIP-Dateien.
5. Dateien, die dein Skript erzeugt (CSV, PNG, …), erscheinen rechts unter **Ergebnisse** zum Herunterladen.

## Layout

- Links (3/4): das Terminal
- Rechts (1/4): Skript, hinzugefügte Dateien, Ergebnisse

## Terminal-Befehle

| Befehl | Wirkung |
|---|---|
| `python3 skript.py [dateien]` | Skript ausführen (`*` und `?` funktionieren als Platzhalter) |
| `ls` | hochgeladene Dateien anzeigen |
| `clear` oder `Strg+L` | Terminal leeren |
| `help` | Hilfe anzeigen |
| Pfeil hoch/runter | frühere Befehle |

## Technik

- [Pyodide](https://pyodide.org) (Python im Browser per WebAssembly), geladen von jsDelivr
- Das Skript läuft in einem Web Worker, die Oberfläche bleibt also bedienbar
- Pakete wie `numpy`, `pandas`, `scipy` oder `matplotlib` werden anhand der `import`-Zeilen automatisch nachgeladen
- Reines HTML, CSS und JavaScript, kein Build-Schritt

## Online stellen mit GitHub Pages

1. Repository erstellen und `index.html` + `README.md` hochladen.
2. **Settings → Pages**, Branch `main` und Ordner `/ (root)` auswählen.
3. Nach kurzer Zeit ist die Seite unter `https://<dein-name>.github.io/<repo>/` erreichbar.

## Einschränkungen

- Beim ersten Start wird Python (ca. 10 MB) aus dem Internet geladen. Danach ist der Browser-Cache schneller.
- Es gibt nur Pakete, die Pyodide anbietet. Reine Python-Pakete lassen sich nicht per `pip` nachinstallieren.
- Keine Eingaben im Skript (`input()`) und kein Zugriff auf echte Systembefehle. Das Terminal kennt nur die oben genannten Befehle.
- Sehr große ZIP-Dateien brauchen viel Arbeitsspeicher, weil sie im Browser gehalten werden.
- Das Skript läuft in einem frischen Ordner. Zwischen zwei Ausführungen bleiben keine Dateien erhalten.

## Lizenz

Wähle eine Lizenz für dein Repository (z. B. MIT) und füge eine `LICENSE`-Datei hinzu.
