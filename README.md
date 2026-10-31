# DLH@School Schaufenster

Öffentliche Kanban-Seite für DLH@School (Fachschaftsberatung und -begleitung).
Alle sehen die Karten. Nur DLH-Mitarbeitende mit Schreibrecht auf dieses Repository können Karten erfassen, bearbeiten und verschieben.

## So funktioniert der Schutz

- Die Karten liegen in `data/begleitungen.json` in diesem Repository.
- Besucherinnen und Besucher laden diese Datei nur lesend.
- Wer bearbeiten will, meldet sich über «Team-Login» (unten auf der Seite) mit einem persönlichen GitHub-Token an. Die Seite speichert jede Änderung als Commit über die GitHub-API.
- GitHub prüft bei jedem Speichern, ob das Token Schreibrecht hat. Ohne Schreibrecht wird nichts gespeichert, egal was jemand im Browser verändert.
- Jede Änderung ist in der Commit-Historie mit Person und Zeitpunkt nachvollziehbar und lässt sich rückgängig machen.

## Einrichten (einmalig, Repository-Inhaber)

1. Repository anlegen, z. B. `dlh-at-school`, und `index.html` sowie den Ordner `data/` hochladen.
2. In `index.html` oben im Skript `CONFIG.owner` und `CONFIG.repo` anpassen.
3. GitHub Pages aktivieren: Settings → Pages → Branch `main`, Ordner `/ (root)`.
4. Jede Begleitperson unter Settings → Collaborators mit Rolle «Write» einladen.

## Zugang für Begleitpersonen (einmalig, pro Person)

1. GitHub-Konto anlegen (falls noch keines) und die Einladung annehmen.
2. Fine-grained Token erstellen: GitHub → Settings → Developer settings → Fine-grained tokens → «Generate new token».
   - Resource owner: der Account des Repositorys
   - Repository access: «Only select repositories» → nur dieses Repository
   - Permissions: «Contents» → «Read and write»
   - Ablaufdatum: z. B. Ende Schuljahr
3. Auf der Seite «Team-Login» wählen und das Token einfügen.

Das Token nie weitergeben und nicht in Dateien speichern. Bei Verlust auf GitHub löschen und neu erstellen.

## Wichtig zum Datenschutz

Das Repository ist öffentlich, inklusive aller früheren Versionen. Deshalb gehören keine Namen von Lehrpersonen, keine E-Mail-Adressen und keine internen Notizen auf die Karten. Diese Angaben bleiben in der Jahresübersicht und in OneNote.

## Hinweise

- Nach dem Speichern sehen angemeldete Personen die Änderung sofort. Für Besucherinnen und Besucher kann es bis zu etwa 10 Minuten dauern (Zwischenspeicher von GitHub Pages).
- Karten ziehen funktioniert mit der Maus. Auf Tablet und Handy die Karte antippen und den Status im Formular ändern.
