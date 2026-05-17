# satori-web

Statische Mini-Site für die satori-App. Enthält:

* `index.html` — schlichte Landing-Page
* `privacy.html` — DSGVO-Datenschutzerklärung
* `impressum.html` — § 5 TMG / § 18 MStV Impressum
* `style.css` — Sumi-e-inspirierter Style (Cream/Ink/Gold, light + dark)

Wird über **GitHub Pages** gehostet und in der App Store Connect
Privacy-Policy-URL referenziert.

---

## Bevor du pushst: Platzhalter füllen

In `index.html`, `privacy.html`, `impressum.html` gibt es eckige
Platzhalter, die mit echten Daten ersetzt werden müssen. Such+ersetz
über alle Dateien:

| Platzhalter | Beispielwert |
|---|---|
| `[VORNAME NACHNAME]` | `Alessandro Mustermann` |
| `[STRASSE HAUSNR]` | `Musterstraße 42` |
| `[PLZ ORT]` | `70173 Stuttgart` |
| `[LAND, z. B. Deutschland]` | `Deutschland` |
| `[LAND]` | `Deutschland` |
| `[EMAIL-PLATZHALTER]` | `hallo@satori-app.de` (oder deine echte) |
| `[DATUM-PLATZHALTER, z. B. 17. Mai 2026]` | `17. Mai 2026` |
| `[BUNDESLAND-PLATZHALTER]` | `Baden-Württemberg` |
| `[AUFSICHTSBEHÖRDE-PLATZHALTER]` | siehe unten |

### Aufsichtsbehörden je nach Bundesland

Die zuständige Aufsichtsbehörde hängt von deinem Wohnsitz / Sitz ab.
Wenn du z. B. in Baden-Württemberg wohnst:

```
Der Landesbeauftragte für den Datenschutz und die Informationsfreiheit
Lautenschlagerstraße 20, 70173 Stuttgart
Telefon: 0711 / 615541-0
E-Mail: poststelle@lfdi.bwl.de
Web: baden-wuerttemberg.datenschutz.de
```

Vollständige Liste aller Landesbeauftragten:
<https://www.bfdi.bund.de/DE/Service/Anschriften/Laender/Laender-node.html>

In `impressum.html` ist im Block „Verantwortlich für den Inhalt" der
Name nochmal — bitte gleich mitanpassen.

---

## GitHub Pages aktivieren (einmalig)

1. Repository erstellen, z. B. `satori-web` unter deinem GitHub-Account
2. Diese Dateien committen + pushen
3. Repository-Settings → **Pages** → Source: `Deploy from a branch`
   → Branch: `main`, Folder: `/ (root)` → Save
4. Nach 1–2 Minuten ist die Seite live unter:
   `https://<dein-username>.github.io/satori-web/`
5. Optional: in den Pages-Settings „Enforce HTTPS" aktivieren
   (sollte automatisch an sein)

### URLs für ASC + In-App

Nach Aktivierung kannst du folgende URLs verwenden:

```
https://<dein-username>.github.io/satori-web/privacy.html
https://<dein-username>.github.io/satori-web/impressum.html
```

Diese trägst du in:

* **App Store Connect** → App-Information → „Privacy Policy URL"
  → die `privacy.html`-URL
* **App Store Connect** → App-Information → „Marketing URL" (optional)
  → die Root-URL
* **In der App** ist der Inhalt bereits doppelt gehalten (siehe
  `Localizable.xcstrings` Keys `legal.privacy.body` und
  `legal.imprint.body`) — wenn du den Web-Text änderst, prüfe auch
  diese beiden String-Catalog-Einträge auf Konsistenz.

---

## Später (optional): Custom Domain `satori-app.de`

Wenn du die Domain registriert hast:

1. Domain bei deinem DNS-Provider auf GitHub Pages zeigen lassen:
   * Apex `satori-app.de` → 4 A-Records auf 185.199.108.153,
     185.199.109.153, 185.199.110.153, 185.199.111.153
   * `www.satori-app.de` → CNAME auf `<dein-username>.github.io`
2. Im Repo eine Datei `CNAME` (kein Suffix!) anlegen mit Inhalt:
   ```
   satori-app.de
   ```
3. Repository-Settings → Pages → Custom domain: `satori-app.de` →
   Save. Nach DNS-Propagation (kann 1–24h dauern) live.
4. „Enforce HTTPS" ankreuzen.
5. Privacy-URL in App Store Connect auf `https://satori-app.de/privacy.html`
   ändern, bei nächstem App-Update einreichen.

---

## Wahrheits-Quelle für den Datenschutz

Diese Privacy-Page ist eine konsumentenfreundlich gerenderte Version
der zentralen Doku in der iOS-App-Repo:

```
/Users/alessandro/Code/satori/concept/datenschutz.md
```

Wenn sich die Datenerhebung der App ändert, dort zuerst pflegen — und
dann hier (`privacy.html`) und in der App (`legal.privacy.body`) nachziehen.
