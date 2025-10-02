# testflask

Projekt testuje virtuální prostředí a instalaci závislostí.

Setup

1. Aktivace v Linux / macOS:

```bash
source .venv/bin/activate
```

2. Instalace (pokud chcete znovu):

```bash
pip install -r requirements.txt
```

Jak otestovat

Ověřte, že `flask` a `requests` jsou importovatelné:

```bash
python -c "import flask, requests; print(flask.__version__, requests.__version__)"
```

Spuštění lokálního Flask serveru

1. Nastavte URL na transkripční API (výchozí ukazuje na https://aivoie.sspu-opava.cz):

```bash
export TRANSCRIBE_API_URL=https://aivoie.sspu-opava.cz
# volitelně nastavte tajný klíč
export FLASK_SECRET="change-me"
```

2. Spusťte aplikaci

```bash
python app.py
```

3. Otevřete prohlížeč na http://localhost:5000 a nahrajte audio soubor.

API manual: http://192.168.22.141:9010

Poznámka: virtuální prostředí je ve složce `.venv`. Doporučujeme přidat `.venv/` do `.gitignore` pokud chcete.
