Here’s a tighter, “viral-ready” README with stronger positioning, clearer hooks, and GitHub-friendly structure (badges, quick wins, tone, scannability).

---

# ⚡ mlx — Ollama-style CLI for Apple MLX

> Run local LLMs on Apple Silicon — **fast, simple, no Docker**

[![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon-black?logo=apple)](#)
[![MLX](https://img.shields.io/badge/Powered%20by-MLX-blue)](#)
[![Python](https://img.shields.io/badge/Python-3.12+-yellow)](#)
[![License](https://img.shields.io/badge/license-MIT-green)](#)

---

## 🚀 What is this?

`mlx` is a **minimal, zero-bloat CLI** that brings an **Ollama-like experience** to Apple's **MLX ecosystem**.

No containers. No Node. No nonsense.

Just:

```bash
mlx pull -m mlx-community/Qwen2.5-Coder-7B-Instruct-4bit
mlx chat
```

---

## ✨ Why mlx?

* 🍏 **Built for Apple Silicon (M1–M4)**
* ⚡ **Blazing fast via MLX (Metal)**
* 🧠 **Run HuggingFace models directly**
* 📦 **One-command setup**
* 🛠 **Pure Bash (no runtime lock-in)**
* 🔥 **Feels like Ollama — but native**

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
| Apple MLX   | ✅   | ❌      |
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
