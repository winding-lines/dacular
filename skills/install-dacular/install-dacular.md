---
name: install-dacular
description: Install and configure the Dacular local AI stack (zeroclaw + Modular Max + Gemma3) on a Mac mini
version: 0.1.0
platform: darwin
hardware: mac-mini
---

# install-dacular

> **Status: placeholder** — This skill is under active development.

This skill guides you through setting up Dacular — a local AI stack running [zeroclaw](https://github.com/zeroclaw) and [Modular Max](https://www.modular.com/max) with Gemma3 inference on a Mac mini.

## What this skill does

1. Creates a dedicated macOS user account for the AI stack (isolated from your personal data)
2. Installs and configures zeroclaw (agent framework)
3. Installs Modular Max with Gemma3 as the local inference engine
4. Wires zeroclaw to Max so agents can run inference locally
5. Sets up a data workflow: mount your data from the main account, do your work, then unmount before starting Claude — so private data is never accessible while Claude is running

## Usage

```
/install-dacular
```

## Requirements

- Mac mini (Apple Silicon recommended)
- macOS 14 (Sonoma) or later
- Administrator access to create a new user account

## Coming soon

- Step-by-step guided installation
- Automated configuration of zeroclaw ↔ Max integration
- Secure data mount/unmount lifecycle management
