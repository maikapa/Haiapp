# Hai — Einspielen auf GitHub Pages

## Einmalig einrichten

1. Neues Repository anlegen, zum Beispiel `hai`.
2. Den Inhalt dieses Ordners ins Repository legen — `index.html` muss im Wurzelverzeichnis liegen,
   nicht in einem Unterordner.
3. Committen und pushen:

       git init
       git add .
       git commit -m "Hai-App"
       git branch -M main
       git remote add origin git@github.com:DEINNAME/hai.git
       git push -u origin main

4. Auf GitHub: Settings → Pages → Source: `Deploy from a branch`,
   Branch `main`, Ordner `/ (root)`, speichern.
5. Nach ein bis zwei Minuten liegt die App unter
   `https://DEINNAME.github.io/hai/`.

## Aufs alte iPad bringen

Adresse in Safari öffnen, Teilen-Knopf, „Zum Home-Bildschirm". Danach startet die App
im Vollbild ohne Adressleiste. Das Icon kommt aus `icon-180.png`.

## Was die Dateien tun

- `index.html` — das komplette Spiel, eine einzige Datei, keine Abhängigkeiten
- `manifest.webmanifest` — Name, Icon und Vollbildmodus für den Home-Bildschirm
- `icon-180/192/512.png` — App-Icons
- `.nojekyll` — verhindert, dass GitHub Pages die Dateien durch Jekyll schickt

## Spielstände

Die Spielstände liegen im localStorage des jeweiligen Geräts, ein Eintrag je Kinderprofil.
Sie wandern nicht zwischen Handy und iPad. Ein neues Deployment löscht sie nicht,
solange die Adresse gleich bleibt.

## Aufbau des Spiels

Der Hai taucht immer tiefer. Jede Tiefe hat genau eine Gefahrenart und einen Boss.
Ist der Boss geknackt, wird ein gefangenes Meerestier frei und schwimmt ab dann
dauerhaft im Heimatriff. Die ersten zwoelf Tiefen sind von Hand gesetzt
(`LEVELS`), danach werden sie aus Bausteinen kombiniert (`HAZ_POOL`, `BOSSES`,
`PALETTES`) — das laeuft endlos weiter.

## Werte zum Nachjustieren

Ganz oben im `<script>` von `index.html`:

- `FISH_PER_CARD` — nach wie vielen Fischen eine Aufstiegskarte kommt (aktuell 10)
- `FISH_FOR_BOSS` — nach wie vielen Fischen der Boss auftaucht (aktuell 40)
- `MAX_LEVEL` — Stufen je Fähigkeit (aktuell 5)
- `MAX_BONUS` — höchste dauerhafte Startstufe (aktuell 2)
