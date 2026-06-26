# Llama_Dispatcher – Instance: Laptop

Dieses private Repository enthält die maschinenspezifische Konfiguration der Instanz **Laptop**
für den [Llama_Dispatcher](https://github.com/SomeSunlight/Llama_Dispatcher).

## Inhalt

| Verzeichnis / Datei | Beschreibung |
|---|---|
| `instance.yaml` | Machine-GUID und Nickname dieser Instanz |
| `profiles/` | YAML-Profile (llama.cpp-Startparameter) für diese Maschine |
| `ensembles/` | YAML-Ensembles (Zusammenstellungen mehrerer Profile) |
| `engines/` | Engine-Konfiguration (Vulkan / SYCL / CUDA) |
| `data/metrics.db` | SQLite-Datenbank mit Benchmark- und Laufzeit-Metriken |
| `data/thinkpad_models.ini` | Modell-Preset-Datei für llama-server (Multi-Model-Router) |

## Zugehöriger Dispatcher

Der Dispatcher selbst (Code, Defaults, Dokumentation) liegt im öffentlichen Repo:
→ https://github.com/SomeSunlight/Llama_Dispatcher

## Setup auf neuem Rechner

Das Hauptrepo und die Instanz-Repos müssen in die **exakt richtigen Verzeichnisse** geklont werden.
Der Trick: `git clone <url> <zielverzeichnis>` akzeptiert einen eigenen Ordnernamen.

```powershell
# 1. Hauptrepo klonen
git clone https://github.com/SomeSunlight/Llama_Dispatcher.git
cd Llama_Dispatcher

# 2. Diese Instanz in das korrekte Unterverzeichnis klonen
#    (GitHub würde sonst "Llama_Dispatcher_Laptop" als Ordner anlegen – falsch!)
git clone https://github.com/SomeSunlight/Llama_Dispatcher_Laptop.git instances/Laptop

# 3. Python-Umgebung einrichten
uv sync
```

Danach muss `instance.yaml` auf die neue `machine_guid` dieser Maschine aktualisiert werden
(oder eine neue Instanz unter anderem Namen angelegt werden).

## Nutzung

```bash
uv run src/dispatcher.py serve --ensemble <name> --instance Laptop
```

## Lizenz

MIT – nur relevant falls dieses Repo jemals veröffentlicht wird.

