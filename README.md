# Local ChatGPT Clone on Mac with Ollama and OpenWebUI

Run your own private ChatGPT style chatbot on your Mac using:
- Ollama for local models
- OpenWebUI for a clean chat interface
- Docker Desktop for managing the web UI container

## Features

- 100 percent local inference on your machine.
- No API keys.
- No monthly subscription.
- Full control of which models you run.
- Works offline once models are downloaded.
- Can be extended with MCP tools later for search and custom integrations.

## Stack

- macOS
- Docker Desktop
- Ollama
- OpenWebUI
- Models:
  - DeepSeek (reasoning and coding)
  - Llama (general chat)
  - nomic-embed-text (embeddings for search and retrieval)

## Prerequisites

- macOS with admin access.
- Docker Desktop installed and running.
- Ollama installed on Mac.
- At least 16 GB RAM recommended.
- Sufficient disk space for model downloads.

## Installation

### 1. Install Docker Desktop

1. Download Docker Desktop for Mac from the official Docker website.  [Download Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Install and open Docker.
3. Wait until the Docker whale icon appears and shows that Docker is running.

### 2. Install Ollama

1. Download Ollama for macOS from the official Ollama website.  [Download Ollama](https://ollama.com/download)
2. Install and open Ollama once to complete setup.
3. Verify from Terminal:

   ```bash
   ollama --version
   ```

### 3. Pull models with Ollama

In Terminal:

```bash
ollama pull deepseek-r1
ollama pull llama3.1
ollama pull nomic-embed-text
```

You only need one main chat model — either DeepSeek or Llama — but you can install both if you want to compare them.

Quick test:

```bash
ollama run llama3.1
```

Ask a question, then exit with Ctrl + C.

### 4. Run OpenWebUI with Docker

```bash
docker pull ghcr.io/open-webui/open-webui:main
```

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data --name open-webui ghcr.io/open-webui/open-webui:main

```

Open in your browser:

- http://localhost:3000

Follow the initial setup in OpenWebUI. It should auto detect your Ollama models.

## Models

### DeepSeek

- Great for reasoning and code heavy tasks.
- Use it when you want step by step analysis and problem solving.

### Llama

- Balanced general purpose model.
- Use it for everyday chat, learning, and explanation type prompts.

### nomic-embed-text

- Embedding model for semantic search and retrieval.
- Use it behind the scenes when building features like:
  - document search
  - question answering over your own notes
  - retrieval augmented generation (RAG)

## MCP

This setup can later be extended with MCP (Model Context Protocol) compatible tools.

Ideas:
- Add a file search tool that lets the model read and answer questions about documents.
- Add a web search tool for live information.
- Add custom API tools for your own services.

## Troubleshooting

- If Docker says the port is already in use, change `-p 3000:8080` to another host port, for example `-p 3001:8080`.
- If OpenWebUI does not see your models, check:
  - Ollama is running.
- If models are slow:
  - Close other heavy apps.
  - Try a smaller model variant if available.

## Author
**Jawwad Ahmed Abbasi**  
Senior Software Developer  
[GitHub](https://github.com/jawwadabbasi) | [YouTube](https://www.youtube.com/@jawwad_abbasi)