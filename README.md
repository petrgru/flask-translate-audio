# Flask Audio Transcription

Jednoduchá Flask aplikace pro nahrávání audio souborů a jejich přepis na text pomocí API.

## Struktura projektu

```
.
├── app.py              # Flask aplikace
├── requirements.txt    # Python závislosti
├── templates/         
│   ├── upload.html    # Formulář pro nahrání souboru
│   └── result.html    # Zobrazení výsledku přepisu
└── uploads/           # Složka pro dočasné audio soubory
```

## Instalace

1. Vytvořte a aktivujte virtuální prostředí:

```bash
# Vytvoření venv
python3 -m venv .venv

# Aktivace v Linux/macOS
source .venv/bin/activate

# Aktivace ve Windows
.venv\Scripts\activate
```

2. Instalace závislostí:

```bash
pip install -r requirements.txt
```

## Konfigurace

Aplikace používá konfigurační soubor `.env` pro nastavení proměnných prostředí. Výchozí hodnoty najdete v `.env.example`:

1. Zkopírujte šablonu do `.env`:
```bash
cp .env.example .env
```

2. Upravte hodnoty v `.env` podle potřeby:
```ini
# API Configuration
TRANSCRIBE_API_URL=http://192.168.22.141:9000
TRANSCRIBE_ENDPOINT=/transcribe
TRANSCRIBE_API_MANUAL=http://192.168.22.141:9010

# Flask Configuration
FLASK_SECRET=change-me-in-production
PORT=5000

# Upload Configuration
KEEP_UPLOADS=0
UPLOAD_DIR=uploads
```

Vysvětlení proměnných:

| Proměnná | Výchozí hodnota | Popis |
|----------|----------------|--------|
| `TRANSCRIBE_API_URL` | `http://192.168.22.141:9000` | URL transkripčního API serveru |
| `TRANSCRIBE_ENDPOINT` | `/transcribe` | Endpoint pro transkripci na API serveru |
| `TRANSCRIBE_API_MANUAL` | `http://192.168.22.141:9010` | URL manuálu API |
| `FLASK_SECRET` | `dev-secret` | Tajný klíč pro Flask session |
| `PORT` | `5000` | Port pro Flask server |
| `KEEP_UPLOADS` | `0` | Zachovat nahrané soubory (1=ano, 0=ne) |
| `UPLOAD_DIR` | `uploads` | Adresář pro nahrané soubory |

**Poznámka**: Soubor `.env` není verzován v gitu. Použijte `.env.example` jako šablonu.

## Spuštění

1. Aktivujte venv a spusťte aplikaci:

```bash
source .venv/bin/activate
python app.py
```

2. Otevřete prohlížeč na http://localhost:5000

## Použití

1. V prohlížeči vyberte audio soubor
2. Zvolte jazyk (`en` nebo `cz`)
3. Nastavte teplotu (0.0 - 1.0)
4. Klikněte na "Transcribe"
5. Výsledný přepis se zobrazí na další stránce

## API Dokumentace

- API Server: http://192.168.22.141:9000
- API Manuál: http://192.168.22.141:9010

## Řešení problémů

1. **404 Not Found**: Zkontrolujte `TRANSCRIBE_ENDPOINT` - musí odpovídat API serveru
2. **Connection Error**: Ověřte `TRANSCRIBE_API_URL` a dostupnost serveru
3. **Template Not Found**: Zkontrolujte že existuje složka `templates/` se soubory `upload.html` a `result.html`
4. **Permission Error**: Zkontrolujte práva pro zápis do složky `uploads/`

## Vývoj

- `.venv/` je v `.gitignore`
- Nahrané soubory jsou ve výchozím nastavení mazány po odeslání
- Pro zachování souborů nastavte `KEEP_UPLOADS=1`
