# Tech Stack

## Overview
Single-file vanilla web app — no build system, no bundler, no dependencies to install. Everything lives in one HTML file.

## Stack
- **HTML/CSS/JavaScript** — pure vanilla, no frameworks
- **Anthropic Claude API** — `claude-sonnet-4-20250514` via `fetch()` directly from the browser
  - Endpoint: `https://api.anthropic.com/v1/messages`
  - API key must be handled client-side (hackathon context)
- **Google Fonts** — Sora and Noto Sans MY loaded via CDN

## API Integration
- Direct browser-to-API calls using `fetch()` with `POST` to Anthropic's messages endpoint
- Request shape: `{ model, max_tokens, system, messages }`
- Conversation history maintained in a `conversationHistory` array (in-memory, resets on page reload)
- Context (location, time, mood, budget) is prepended to each user message as a bracketed note

## No Build / No Commands
There is no build step, package manager, or test runner. To run the app:
- Open `my-buddy.html` directly in a browser, or
- Serve it with any static file server (e.g., `npx serve .` or VS Code Live Server)

## CSS Architecture
- CSS custom properties (variables) defined on `:root` for the full design token set
- Malaysian flag-inspired color palette: `--jalur-red`, `--bulan-gold`, `--bintang-blue`
- Dark theme only (`--bg: #0a0f1e`)
- No CSS preprocessor — plain CSS in a `<style>` block within the HTML file
