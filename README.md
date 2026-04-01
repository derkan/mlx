
# ⚡ mlx — Ollama-style CLI for Apple MLX

> Run local LLMs on Apple Silicon — **fast, simple, no Docker**

[![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon-black?logo=apple)](#)
[![MLX](https://img.shields.io/badge/Powered%20by-MLX-blue)](#)
[![Python](https://img.shields.io/badge/Python-3.12+-yellow)](#)
[![License](https://img.shields.io/badge/license-MIT-green)](#)

---

## 🚀 What is this?

`mlx` is a **minimal, zero-bloat CLI** bash script that brings an **Ollama-like experience** to Apple's **MLX ecosystem** using [mlx.lm](https://github.com/ml-explore/mlx-lm)

No containers. No Node. No nonsense.

Just:

```bash
mlx pull -m mlx-community/Qwen2.5-Coder-7B-Instruct-4bit
mlx chat
```

---

## ✨ Why mlx?

* 🍏 **Built for Apple Silicon**
* ⚡ **Blazing fast via MLX (Metal)**
* 🧠 **Run HuggingFace models directly**
* 📦 **One-command setup**
* 🛠 **Pure Bash (no runtime lock-in)**
* 🔥 **Feels like Ollama**

---

## ⚡ 30-Second Setup

```bash
chmod +x mlx
./mlx install
```

Then:

```bash
mlx pull -m mlx-community/Qwen2.5-Coder-7B-Instruct-4bit --alias coder
mlx chat -m coder
```

Done.

---

## 🎬 Demo (what it feels like)

```bash
mlx run codex
```

```
> write a Go HTTP server

package main
import "net/http"
...
```

---

## 🧠 Core Commands

```bash
mlx install                 # bootstrap everything
mlx pull -m MODEL          # download model
mlx ls                     # list models
mlx chat                   # interactive chat
mlx serve                  # background server
mlx stop                   # stop server
mlx run codex              # coding preset
mlx search                 # search for models at HuggingFace 
```

---

## 📦 Model Management

```bash
mlx pull -m mlx-community/Qwen2.5-Coder-7B-Instruct-4bit --alias coder
mlx ls
mlx rm -m coder
```

---

## 💬 Chat (like Ollama)

```bash
mlx chat -m coder
```

With tuning:

```bash
mlx chat -m coder \
  --temperature 0.2 \
  --max-kv-size 4096 \
  --trust-remote-code
```

---

## 🚀 Server Mode

```bash
mlx serve -m coder
mlx status
mlx logs
mlx stop
```

---

## Model Search

```bash
mlx search
mlx search --fit
mlx search --best
mlx search --fit --limit 50
mlx search --fit --ram 48
mlx search --json
mlx search --refresh
mlx search --community-only
mlx search --author lmstudio-community
```

> mlx search --fit is an estimate based on model repo metadata, quantization hints, weight sizes, and available RAM. It is meant to be useful and conservative, not perfect.

Useful flags:

```bash
mlx search --fit           # only models likely to fit this machine
mlx search --best          # best near-term picks
mlx search --ram 48        # override auto-detected RAM
mlx search --limit 50      # fetch more repos
mlx search --refresh       # bypass cache
mlx search --json          # machine-readable output
```

Example:

```bash
mlx search --fit
```

Output:
```bash
MODEL                                                          WT_GB  FIT       AGE   UPDATED NOTES
mlx-community/Qwen2.5-Coder-7B-Instruct-4bit                     4.8   ✅        2mo       3d coding, 4bit
mlx-community/Llama-3.1-8B-Instruct-4bit                        5.2   ✅        4mo       1w 4bit
mlx-community/Qwen2.5-Coder-14B-Instruct-4bit                   9.1   ✅        1mo       5d coding, 4bit
mlx-community/Mixtral-8x7B-Instruct-4bit                       26.4   ⚠️        6mo       2w 4bit
```

## 🧰 Presets

```bash
mlx run claude     # reasoning / planning
mlx run codex      # coding (tight output)
mlx run free-code  # creative coding
```

---

## ⚙️ Defaults (tuned for M4 Max 48GB)

| Setting       | Value        |
| ------------- | ------------ |
| Context       | 8192         |
| KV Cache      | 4096         |
| Default Model | Llama-3.2-3B |

---

## 📁 Layout

```bash
~/.local/share/mlx-cli/
  venv/
  models/
  log/
  run/
```

---

## 🧩 Philosophy

* **No magic**
* **No lock-in**
* **No hidden layers**
* Just MLX + Bash

---

## ⚔️ mlx vs Ollama

| Feature     | mlx | Ollama |
| ----------- | --- | ------ |
| Apple MLX   | ✅   | ✅       |
| Docker-free | ✅   | ❌      |
| HF models   | ✅   | ❌      |
| Bash-native | ✅   | ❌      |
| Simplicity  | 🔥  | 🙂     |

---

## 🛠 Troubleshooting

```bash
mlx doctor
```

If Python fails:

```bash
xcode-select --install
```

---

## 🧨 Uninstall

```bash
mlx uninstall
```

---

## 🔐 Hugging Face Token (Optional but Recommended)

Using an `HF_TOKEN` significantly improves download reliability and avoids rate limits.

### 1. Get your token

1. Go to: [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)
2. Click **“New token”**
3. Select:

   * **Type:** `Read`
4. Create and copy the token

---

### 2. Set it in your shell

```bash
export HF_TOKEN="hf_xxxxxxxxxxxxxxxxx"
```

Persist it:

#### Bash

```bash
echo 'export HF_TOKEN="hf_xxx"' >> ~/.bashrc
```

#### Zsh

```bash
echo 'export HF_TOKEN="hf_xxx"' >> ~/.zshrc
```

Then reload:

```bash
source ~/.bashrc   # or ~/.zshrc
```

---

### 3. Verify

```bash
echo $HF_TOKEN
```

---

### Notes

* Required for **gated/private models**
* Avoids **429 rate limits**
* Speeds up downloads via authenticated requests
* Used automatically by `mlx` / `huggingface_hub` if present

## 🗺 Roadmap

* [ ] OpenAI-compatible API
* [ ] Streaming responses
* [ ] launchd service mode
* [ ] prompt templates
* [ ] shell completion

---

## 🤝 Contribute

PRs welcome — especially:

* performance tuning
* model UX improvements
* MLX integrations

---

## 📜 License

MIT

---

## ⭐ If this saved you time...

Give it a star.
