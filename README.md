# Wasteland Waifus – GitHub Pages Deployment

Dieser Ordner enthält alles fertig für GitHub Pages:

```
index.html              ← das Spiel
manifest.json           ← Web-App-Manifest (Installierbarkeit)
sw.js                   ← Service Worker (Offline-Caching)
icon-192.png            ← App-Icon klein
icon-512.png            ← App-Icon groß
icon-512-maskable.png   ← App-Icon für runde/adaptive Icons (Android)
```

## So geht's (5 Minuten, ohne Kommandozeile)

1. **Repo erstellen:** Auf [github.com](https://github.com) einloggen → oben rechts **"+"** → **"New repository"**.
   Name z. B. `wasteland-waifus` → **Public** auswählen → "Create repository".

2. **Dateien hochladen:** Im neuen, leeren Repo auf **"uploading an existing file"** klicken
   (oder "Add file" → "Upload files"). Alle 6 Dateien aus diesem Ordner per Drag & Drop reinziehen
   (README.md kann mit hochgeladen werden, stört nicht). Unten auf **"Commit changes"** klicken.

3. **GitHub Pages aktivieren:** Im Repo auf **"Settings"** → links **"Pages"**.
   Unter "Build and deployment" → "Source" → **"Deploy from a branch"** wählen.
   Branch: **`main`**, Ordner: **`/ (root)`** → **"Save"**.

4. **Kurz warten:** Nach ca. 1–2 Minuten steht oben auf der Pages-Einstellungsseite ein grüner Kasten
   mit dem Link, z. B.:
   `https://DEIN-USERNAME.github.io/wasteland-waifus/`

5. **Fertig.** Link öffnen (auf dem Handy oder Desktop) → oben links auf **"📲 App"** tippen →
   jetzt läuft der native Installieren-Dialog des Browsers zuverlässig (funktioniert dank
   `manifest.json` + `sw.js` jetzt auch bei Chrome ohne Umwege), und das Spiel läuft danach
   auch **offline**, weil der Service Worker alle Dateien einmal im Browser cached.

## Updates später hochladen

Einfach im Repo die geänderte `index.html` (oder andere Datei) erneut hochladen/committen —
GitHub Pages deployed automatisch neu (dauert wieder ~1 Minute). Der Service Worker verwendet
die Cache-Version `wasteland-waifus-v1` in `sw.js` — wird der Code des Spiels grundlegend
geändert, einfach `v1` auf `v2` hochzählen, damit alte Browser-Caches nicht kleben bleiben.

## Warum GitHub Pages besser ist als die Artifact-Vorschau

- Eigene, feste URL statt Sandbox-Link
- `manifest.json` und `sw.js` sind echte, eigenständige Dateien auf derselben Domain —
  das ist die technische Voraussetzung dafür, dass Chrome/Edge den "App installieren"-Dialog
  zuverlässig anbietet und das Spiel offline funktioniert
- Kostenlos, kein eigener Server nötig
