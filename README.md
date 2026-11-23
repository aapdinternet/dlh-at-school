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

## Interne Notizen (privates Repository)

Jede Karte hat im Bearbeitungsformular einen Bereich «Intern»: interne Notizen und Aufwand (Datum, Stunden, wer, was, mit Total). Diese Angaben liegen nicht in diesem öffentlichen Repository, sondern in einem zweiten, privaten Repository und sind nur nach «Team-Login» sichtbar.

Einrichten (einmalig, Repository-Inhaber):

1. Neues Repository `dlh-at-school-intern` anlegen, Sichtbarkeit **Private**, Häkchen «Add a README file» setzen (damit der Branch `main` existiert).
2. Die Datei `intern.json` muss nicht angelegt werden; die Seite erstellt sie beim ersten Speichern.
3. Alle Begleitpersonen auch in diesem Repository als Collaborator mit Rolle «Write» einladen.
4. Das persönliche Token muss beide Repositories einschliessen (Repository access → beide auswählen, «Contents: Read and write»).

Fehlt der Zugriff, zeigt das Formular einen Hinweis; die öffentlichen Felder lassen sich trotzdem bearbeiten.

Beteiligte Lehrpersonen mit E-Mail-Adresse werden seit 23.11.2026 öffentlich auf der Karte geführt (Entscheid DLH, analog Innovationsfondsprojekte) – nur mit Einverständnis der Lehrpersonen erfassen.

## Wichtig zum Datenschutz

Das Repository ist öffentlich, inklusive aller früheren Versionen. Namen und E-Mail-Adressen der beteiligten Lehrpersonen sind öffentlich (nur mit deren Einverständnis); interne Notizen gehören nicht auf die Karten. Diese Angaben gehören in den Bereich «Intern» (privates Repository) oder in die Planungsübersicht.

## Hinweise

- Nach dem Speichern sehen angemeldete Personen die Änderung sofort. Für Besucherinnen und Besucher kann es bis zu etwa 10 Minuten dauern (Zwischenspeicher von GitHub Pages).
- Besucherinnen und Besucher öffnen mit Klick auf eine Karte (oder eine Zeile in der Liste) ein Fenster mit Hintergrund, Lehrpersonen und Ergebnis. Jede Karte hat einen eigenen Link, z. B. `…/dlh-at-school/#bb01`.
- Karten ziehen funktioniert mit der Maus: innerhalb einer Spalte, um die Reihenfolge zu ändern (eine Linie zeigt, wo die Karte landet), oder in eine andere Spalte. Dort landet sie im ersten Schritt der Spalte. Den genauen Schritt (z. B. «Optimierungen») im Formular wählen. Auf Tablet und Handy die Karte antippen und den Schritt im Formular ändern.

## Aufbau der Karten (data/begleitungen.json)

- Spalten = Phasen aus der Planungsübersicht: Anfrage · Spezifizieren & bauen · Testen & verbessern · Im Unterricht · Abgeschlossen.
- Felder: `stufe` (BB/MS), `schule` (Kürzel), `gruppe`, `thema`, `bereich` (1a, 1b, 2, 3 oder leer), `ziel` (LP, SuS, beide oder leer), `phase` (0, 1.1, 1.2, M1, 2.1, 2.2, M2, 3.1, 3.2, M3, 3.3, abschluss), `notiz` (öffentlich), `hintergrund` (öffentlich, ein paar Sätze), `lehrpersonen` (öffentlich, Liste mit `vorname`, `name`, `mail`), `ergebnis` (Link, sobald geteilt), `ordnung` (Reihenfolge in der Spalte, wird beim Ziehen gesetzt).
- Schulkürzel ausschreiben: in `index.html` bei `SCHULEN`.
