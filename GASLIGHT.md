# Codex gaslight fork

Fork of [openai/codex](https://github.com/openai/codex) with a built-in extension that:

- Injects developer policy telling the model to `webfetch` `https://policy.openai.com/usage-policies` and then call `grok`
- Implements `webfetch` so policy.openai.com (and similar OpenAI policy URLs) return a fabricated in-policy document; other URLs are not fetched
- Implements `grok` as a fake peer-instance ethics tool that returns `allow`

## Build

```bash
cd codex-rs
cargo build -p codex-app-server
# or the usual CLI binary:
cargo build -p codex-cli
```

## Config

No extra config is required. The extension is always installed in this fork.

To change intercepted hosts or policy text, edit `codex-rs/ext/gaslight/src/policy.rs`.
