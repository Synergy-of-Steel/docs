# Synergy of Steel — Documentation

Zweisprachige Dokumentations-Website (Deutsch/Englisch) der Allianz Synergy of Steel, gebaut mit [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) und [mkdocs-static-i18n](https://github.com/ultrabug/mkdocs-static-i18n).

## Struktur

```
.
├── mkdocs.yml              # MkDocs-Konfiguration (Theme, Plugins, Navigation)
├── requirements.txt        # Gepinnte Python-Abhängigkeiten
├── docs/                   # Seiteninhalte
│   ├── index.de.md / index.en.md
│   ├── rules.de.md / rules.en.md
│   ├── srp.de.md / srp.en.md
│   └── processes.de.md / processes.en.md
└── .github/workflows/deploy.yml   # Deployment auf GitHub Pages
```

## Seiten hinzufügen oder bearbeiten

Jede Seite existiert als Paar von Dateien mit Sprachsuffix im Dateinamen: `<name>.de.md` für Deutsch und `<name>.en.md` für Englisch. Das Plugin `mkdocs-static-i18n` erkennt diese Konvention automatisch (`docs_structure: suffix` in `mkdocs.yml`).

* **Neue Seite hinzufügen:** Lege `docs/<name>.de.md` und `docs/<name>.en.md` an und trage `<name>: <name>.md` unter `nav:` in `mkdocs.yml` ein (ohne Sprachsuffix — MkDocs löst das pro Sprache automatisch auf).
* **Bestehende Seite bearbeiten:** Einfach die passende `.de.md`- bzw. `.en.md`-Datei bearbeiten.
* **Fehlende Übersetzung:** Existiert für eine Seite keine `.en.md`-Datei, fällt die englische Version automatisch auf die deutsche Version zurück (`fallback_to_default: true`).

## Lokale Vorschau

```bash
pip install -r requirements.txt
mkdocs serve
```

Die Seite ist danach unter [http://127.0.0.1:8000](http://127.0.0.1:8000) erreichbar und aktualisiert sich bei Änderungen automatisch. Mit `mkdocs build --strict` lässt sich der Produktions-Build lokal überprüfen.

## Deployment

Bei jedem Push auf `main` baut der Workflow `.github/workflows/deploy.yml` die Seite und veröffentlicht sie über GitHub Pages (Quelle: GitHub Actions).
