# Llama_Dispatcher – Instance: Laptop

This private repository contains the machine-specific configuration of the **Laptop** instance
for [Llama_Dispatcher](https://github.com/SomeSunlight/Llama_Dispatcher).

## Content

| Directory / File | Description |
|---|---|
| `instance.yaml` | Machine-GUID and nickname of this instance |
| `profiles/` | YAML profiles (llama.cpp startup parameters) for this machine |
| `ensembles/` | YAML ensembles (combinations of multiple profiles) |
| `engines/` | Engine configuration (Vulkan / SYCL / CUDA) |
| `data/metrics.db` | SQLite database with benchmark and runtime metrics |
| `data/thinkpad_models.ini` | Model preset file for llama-server (Multi-Model-Router) |

## Associated Dispatcher

The Dispatcher itself (code, defaults, documentation) is located in the public repo:
→ https://github.com/SomeSunlight/Llama_Dispatcher

## Setup on a New Machine

The main repo and the instance repos must be cloned into the **exact correct directories**.
The trick: `git clone <url> <target_directory>` allows a custom folder name.

```powershell
# 1. Clone main repo
git clone https://github.com/SomeSunlight/Llama_Dispatcher.git
cd Llama_Dispatcher

# 2. Clone this instance into the correct subdirectory
#    (Otherwise GitHub would create "Llama_Dispatcher_Laptop" as a folder – wrong!)
git clone https://github.com/SomeSunlight/Llama_Dispatcher_Laptop.git instances/Laptop

# 3. Set up Python environment
uv sync
```

Afterward, `instance.yaml` must be updated with the new `machine_guid` of this machine
(or a new instance can be created under a different name).

## Usage

```bash
uv run src/dispatcher.py serve --ensemble <name> --instance Laptop
```

## License

MIT – only relevant if this repo is ever published.
