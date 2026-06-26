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

## Nutzung

```bash
uv run src/dispatcher.py serve --ensemble <name> --instance Laptop
```

## Lizenz

MIT – nur relevant falls dieses Repo jemals veröffentlicht wird.

