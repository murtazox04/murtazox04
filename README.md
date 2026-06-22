<h1 align="center">Murtazo Xurramov</h1>

<p align="center">
  <b>Software engineer — systems & AI.</b><br>
  I build the layer that has to be fast and the AI that has to ship.
</p>

---

I'm an **AI Software Engineer at [DOMO](https://domo.uz)** — Uzbekistan's utility super-app
(~2M users) — where I build the assistant and LLM-serving infrastructure behind the product.
That work lives in a private GitLab, so what's public here is the systems side of how I think.

I write **Python** and **Rust**, and I went down to **Mojo** to build the project below.

<br>

## ⚡ mojogram

> A Telegram Bot framework written in **pure Mojo**. No Python in the runtime.

**[murtazox04/mojogram](https://github.com/murtazox04/mojogram)** · **[docs](https://murtazox04.github.io/mojogram/)** · MIT

Mojo gives you static types, value semantics, and real parallelism with no GIL — but no
Python stdlib to stand on. So the foundations are written from scratch:

- **JSON** — hand-written parser + serializer over an arena DOM. **~2.4 µs/op**, **~420K updates/sec**. Adversarial suite: emoji, surrogate pairs, scientific notation, deep nesting, unicode keys.
- **HTTP** — no native TLS in Mojo, so the wire is system `curl` via subprocess, with retry/backoff and `429 retry_after` honored. **~2.3 ms/request** floor — inside Telegram's ~33 ms budget.
- **Concurrency** — opt-in parallel batches via `parallelize`; shared FSM state behind an `Atomic` spinlock. Stress-tested at **500 concurrent writes + 1000 contended read-modify-writes, zero torn state**. ~4× over sequential.
- **Webhooks** — pure-Mojo HTTP server over libc sockets via **FFI**, secret-token validated, tested end-to-end through a real ngrok TLS tunnel and scaled behind nginx.

~60 typed API methods, typed updates over the JSON DOM, composable filters, inline/reply
keyboard builders, Payments + Telegram Stars, i18n with locale fallback, token-bucket rate
limiting. CI runs every suite on each push — pixi + uv, macOS + Linux — tracking a pre-1.0
language.

Not a port. Where Mojo wouldn't express something — no heterogeneous function values, so no
decorator handler registry — I redesigned around the language instead of fighting it.

<br>

## 🛠 Now

- **Production LLM systems** — RAG, agentic loops, MCP servers, eval pipelines, cost-optimized inference for a high-traffic consumer app.
- **Uzbek speech & language** — synthetic Uzbek TTS and an Uzbek-LLM corpus pipeline. Low-resource-language work: most of the fight is data, not modeling.
- **Systems performance** — the thread behind mojogram and my Rust work. Close to the metal, where it pays.

<br>

## 🧰 Stack

```text
Languages   Python · Rust · Mojo
Backend     FastAPI · Django/DRF · async · Taskiq / Celery
Data        PostgreSQL · pgvector · Redis
AI / ML     PyTorch · Hugging Face · vLLM · LoRA/QLoRA · RAG · MCP
Infra       Docker · Kubernetes · GitHub Actions · GCP
```

<br>

## 📬 Connect

[Telegram](https://t.me/murtazo_xurramov) · [LinkedIn](https://linkedin.com/in/murtazo-xurramov) · murtazox04@gmail.com
