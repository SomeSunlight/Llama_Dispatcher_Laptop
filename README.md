# Llama_Dispatcher – Instance: Laptop

This repository contains the machine-specific configuration of the **Laptop** instance for [Llama_Dispatcher](https://github.com/SomeSunlight/Llama_Dispatcher).

## Content

| Directory / File | Description |
|---|---|
| `instance.yaml` | Machine GUID and nickname of this instance |
| `profiles/` | YAML profiles (llama.cpp startup parameters) for this machine |
| `ensembles/` | YAML ensembles (combinations of multiple profiles) |
| `engines/` | Engine configuration (Vulkan / SYCL / CUDA) |

Runtime data deliberately does **not** belong to the instance repository:

- `data/metrics.db` is created locally by the Dispatcher and remains specific to that environment.
- `data/thinkpad_models.ini` is generated from the configured ensemble/profiles and is recreated locally.
- SQLite WAL/SHM files are local runtime state as well.

This keeps Windows and WSL runs separate even when they use the same versioned Laptop configuration.

## Associated Dispatcher

The Dispatcher itself (code, defaults, documentation) is located in the public repo:
https://github.com/SomeSunlight/Llama_Dispatcher

## Setup in a Dispatcher checkout

The main repo and the instance repo must be cloned into the exact expected directories. `git clone <url> <target_directory>` gives the instance repository the required directory name:

```bash
# 1. Clone main repo
git clone https://github.com/SomeSunlight/Llama_Dispatcher.git
cd Llama_Dispatcher

# 2. Clone this instance into the Dispatcher's user-owned instance area
git clone https://github.com/SomeSunlight/Llama_Dispatcher_Laptop.git instances/Laptop

# 3. Set up Python environment
uv sync
```

The Dispatcher creates `instances/Laptop/data/metrics.db` locally when needed. Do not copy another environment's database unless historical metrics are intentionally being migrated.

`instance.yaml` carries the instance identity. When this configuration is reused in a materially different environment, review the identity and all environment-specific paths before running benchmarks.

## Windows and WSL

Profiles and engine settings are versioned because they describe the intended Laptop configuration, but filesystem paths may differ between Windows and WSL. Adapt those paths deliberately for the environment being tested; do not use AI Workstation to rewrite instance configuration behind the Dispatcher's back.

A WSL run should normally keep its own local database even when Windows tests continue in parallel.

## Usage

```bash
uv run src/dispatcher.py serve --ensemble <name> --instance Laptop
```

## License

MIT.
