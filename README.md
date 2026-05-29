# Portfolio_Webpage
Website_Modul_HTML_CSS

This is the first commit.

# stojkov.

Persönliche Portfolio-Website von Kristian Stojkov — Fotograf, Videograf und Visual Storyteller aus Zürich.

---

## Inhalt

```
/
├── index.html
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── main.js
│   └── images/
│       ├── logo_stojkov.svg
│       ├── logo_stojkov_neg.svg
│       ├── 15952392_2160_3840_30fps.mp4
│       └── KristianStojkov_*.jpg
└── README.md
```

---

## Sections

| Section | ID | Beschreibung |
|---|---|---|
| Hero | `#hero` | Fullscreen-Video mit Titel und Logo |
| Gallery | — | Vier ausgewählte Bilder im Grid |
| Projekte | `#projekte` | Drei Projektkarten mit matrix3d-Effekt |
| Skills | `#skills` | Animierte Skill-Balken |
| Erfahrung | `#erfahrung` | Vertikale Timeline |
| Process | `#process` | Vier Schritte horizontal |
| Fotografie | `#fotografie` | 14-Bild-Gallery mit Lightbox |
| About | — | Bild + Text |
| Kontakt | `#contact` | Kontaktformular |

---

## Features

**Dark Mode**
- Automatisch via `prefers-color-scheme`
- Manuell umschaltbar per Toggle-Button im Header
- Auswahl wird in `localStorage` gespeichert
- Theme wird vor dem ersten Paint gesetzt — kein Flackern

**Animationen**
- Hero-Video: sanfter Zoom-In beim Laden + Parallax beim Scrollen
- Alle Sections: `IntersectionObserver` triggert Reveal-Animationen beim Einblenden
- Skill-Balken füllen sich animiert wenn sie sichtbar werden
- Projekt-Bilder: echter `matrix3d`-Tilt der der Mausposition folgt
- Nav-Links: aktiver Link wird beim Scrollen automatisch markiert
- `prefers-reduced-motion` deaktiviert alle Animationen sauber

**Navigation**
- Sticky Header mit Blur-Hintergrund
- Alle Nav-Links führen zu Ankern auf der gleichen Seite
- Burger-Menü auf Mobile

**Fotografie-Lightbox**
- Klick auf jedes Bild öffnet die Lightbox
- Navigation per Pfeil-Buttons oder `←` `→` Tasten
- Schliessen per `✕`, Klick auf Hintergrund oder `Esc`
- Bild-Counter zeigt aktuelle Position

---

## Dark Mode — Farben

| Variable | Light | Dark |
|---|---|---|
| `--color-bg` | `#ffffff` | `#161413` |
| `--color-text` | `#111111` | `#eeece8` |
| `--color-bg-alt` | `#f4f4f2` | `#1e1c1b` |
| `--color-border` | `#dddddd` | `#2e2c2a` |
| `--color-footer-bg` | `#111111` | `#0d0c0b` |

---

## Schrift

**Atkinson Hyperlegible Mono** — eingebunden via Google Fonts.

```html
<link href="https://fonts.googleapis.com/css2?family=Atkinson+Hyperlegible+Mono:ital,wght@0,200..800;1,200..800&display=swap" rel="stylesheet">
```

Wird für Text und Headings gleichermassen verwendet. Gewichte von `200` (Hero-Titel) bis `600` (Buttons, Links).

---

## Abhängigkeiten

| Paket | Version | Zweck |
|---|---|---|
| jQuery | 3.7.1 | Burger-Navigation (`main.js`) |
| Iconoir | latest | Icons (Pfeile, Menü, X) |
| Google Fonts | — | Atkinson Hyperlegible Mono |

Alle externen Ressourcen werden via CDN geladen — keine lokale Installation nötig.

---

## Lokale Entwicklung

Da die Seite ein Hintergrundvideo lädt, braucht es einen lokalen Server (direktes Öffnen der HTML-Datei blockiert Videos in manchen Browsern).

```bash
# mit Python
python3 -m http.server 8000

# mit Node
npx serve .
```

Dann im Browser: `http://localhost:8000`

---

## Bilder ersetzen

Alle Bilder liegen unter `assets/images/`. Die Dateinamen im HTML einfach durch eigene ersetzen:

```html
<!-- vorher -->
<img src="assets/images/KristianStojkov_01.jpg" alt="zh" class="gallery-item" />

<!-- nachher -->
<img src="assets/images/mein-foto.jpg" alt="Beschreibung" class="gallery-item" />
```

Für die 14-Bild-Fotografie-Section dasselbe Prinzip — einfach die `src`-Attribute der `.foto-cell img`-Elemente anpassen.

---

## Inhalte anpassen

**Hero-Text**
```html
<h1>Licht&nbsp;finden,<br>wo keines&nbsp;war.</h1>
```

**Timeline-Einträge** — in der Section `#erfahrung` einfach weitere `.timeline-item`-Blöcke kopieren und Daten anpassen.

**Skill-Balken** — Prozentwert im `data-width`-Attribut und in der `<span>` ändern:
```html
<span class="skill-item__pct">85%</span>
<div class="skill-bar__fill" data-width="85"></div>
```

**Kontaktformular** — das `action`-Attribut des `<form>`-Tags auf den eigenen Backend-Endpunkt oder einen Dienst wie Formspree zeigen lassen.

---

© Kristian Stojkov — Zürich