# FinanceBro 2.2 einrichten (GitHub Pages)

Alles im Browser, kein Terminal, kein Server. Dauert ca. 20 Minuten.

## 1. Vorher: Daten sichern

Die neue Seite bekommt eine neue Adresse, und die Daten wandern nicht von selbst mit.
In deiner **bisherigen** FinanceBro-App: Einstellungen → **Backup als Datei sichern**. Die Datei brauchst du in Schritt 4.

## 2. Auf GitHub hochladen

1. Auf **github.com** ein kostenloses Konto anlegen (oder anmelden).
2. Oben rechts **+ → New repository**.
   Name: `financebro`, Sichtbarkeit: **Public** (nur so ist GitHub Pages kostenlos; deine Finanzdaten liegen nie dort, nur der App-Code).
   **Create repository**.
3. Auf der neuen Seite: **uploading an existing file** (oder *Add file → Upload files*).
   Den **Inhalt** des Ordners `financebro-v2.2` hineinziehen, also `index.html`, `sw.js`, `manifest.json` und die beiden Icons, nicht den Ordner selbst.
   Unten **Commit changes**.
4. Oben **Settings → Pages**.
   Bei *Source*: **Deploy from a branch**, Branch: **main**, Ordner: **/ (root)** → **Save**.
5. Nach 1 bis 2 Minuten steht oben deine Adresse:
   `https://DEIN-NAME.github.io/financebro/`

**Updates später:** im Repository *Add file → Upload files*, die neue `index.html` hochladen, fertig.

## 3. Google einrichten

1. **console.cloud.google.com** → dein FinanceBro-Projekt (oder neues anlegen).
2. **APIs & Dienste → Bibliothek →** „Google Drive API“ aktivieren (falls noch nicht).
3. **Google Auth Platform → Zielgruppe:** Testmodus ist okay, trag dich bei **Testnutzer** mit deiner Gmail-Adresse ein.
4. **Clients → Client erstellen →** Typ **Webanwendung**.
   Bei **„Autorisierte JavaScript-Ursprünge“** eintragen:
   `https://DEIN-NAME.github.io`
   Wichtig: **ohne** `/financebro` und **ohne** Schrägstrich am Ende. Weiterleitungs-URIs brauchst du nicht.
5. Die **Client-ID** kopieren. Ein Secret brauchst du diesmal nicht.

Es kann ein paar Minuten dauern, bis Google die neue Adresse akzeptiert.

## 4. App einrichten

1. Am iPhone in **Safari** `https://DEIN-NAME.github.io/financebro/` öffnen → Teilen → **Zum Home-Bildschirm**.
2. Die App öffnen → Einstellungen → **Backup-Datei laden** → deine Datei aus Schritt 1.
3. Einstellungen → Client-ID einfügen → **Client-ID speichern** → **Mit Google Drive verbinden**.
   Google fragt einmal nach Zustimmung. Den Hinweis „App wurde nicht überprüft“ mit *Weiter* bestätigen, das ist deine eigene App.
4. **Für den Kurzbefehl:** dieselbe Adresse auch einmal in normalem **Safari** öffnen und dort genauso Client-ID eintragen und verbinden.

## So läuft der Abgleich

- Solange die Google-Anmeldung gilt (1 Stunde), gleicht FinanceBro automatisch ab.
- Danach erscheint ein Hinweis „Mit Drive abgleichen“. Antippen, kurz dein Google-Konto bestätigen, fertig. Meist ohne Passwort.
- Einträge gehen nie verloren. Sie warten auf dem Gerät, bis zum nächsten Abgleich.

## 5. Kurzbefehl auf den Sperrbildschirm

In der **Kurzbefehle-App** neuer Kurzbefehl „FinanceBro“:

1. **Nach Eingabe fragen**: Typ *Zahl*, Frage „Betrag?“, Dezimalzahlen erlauben.
2. **Liste** mit deinen Kategorien, genau wie in der App geschrieben.
3. **Aus Liste auswählen**, Aufforderung „Kategorie?“.
4. **URL codieren** mit dem gewählten Eintrag.
5. **Liste** `karte`, `bar` → **Aus Liste auswählen**, Aufforderung „Wie bezahlt?“.
6. **URL**:
   `https://DEIN-NAME.github.io/financebro/?betrag=[Angegebene Zahl]&kat=[Codierte URL]&zahlung=[Gewählter Eintrag]&sofort=1`
7. **URLs öffnen**.

Auf den Sperrbildschirm (iOS 18+): Sperrbildschirm gedrückt halten → **Anpassen** → **Sperrbildschirm** → bei Taschenlampe oder Kamera **–** → **+** → **Kurzbefehl** → FinanceBro.

Die Buchung landet sofort in Safari und beim nächsten Abgleich in Drive und damit auch in der App.
