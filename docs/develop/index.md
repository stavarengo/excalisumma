---
title: ExcaliDash Local Development
description: Set up the ExcaliDash frontend and backend locally to develop a self-hosted Excalidraw workspace.
---

<script setup>
import { setupSlides } from "../.vitepress/theme/screenshot-flows";
</script>

# Local development

Run the backend and frontend in separate terminals.

## Requirements

- Node.js 24.22.1+ (`nvm use` selects the version in `.nvmrc`)
- pnpm 11 (`corepack enable pnpm` activates the version pinned in `package.json`)
- Git

## Install dependencies

From the repository root:

```bash
pnpm install
pnpm install:all
```

## Configure the apps

```bash
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

Replace the generated path placeholders in `backend/.env`:

```dotenv
DATABASE_URL=file:./dev.db
BACKUP_DIR=./backups
```

## Start the backend

```bash
cd backend
pnpm dev
```

## Start the frontend

In another terminal:

```bash
cd frontend
pnpm dev
```

Open `http://localhost:6767`, then follow the first-run screens below. Select the arrows to move from authentication setup through creating an administrator and opening your first drawing.

<ScreenshotCarousel label="First-run setup after starting the local services" :slides="setupSlides" />
