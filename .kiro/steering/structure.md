# Project Structure

## Overview
Minimal single-file project. All application code lives in one HTML file.

```
My-Buddy/
├── my-buddy.html        # Entire application (HTML + CSS + JS)
└── .kiro/
    └── steering/
        ├── product.md   # Product overview and goals
        ├── tech.md      # Tech stack and conventions
        └── structure.md # This file
```

## my-buddy.html Layout
The single file is organized in this order:
1. `<head>` — meta tags, title, Google Fonts CDN link
2. `<style>` — all CSS with `:root` design tokens at the top
3. `<header>` — sticky top bar with branding and status dot
4. `.context-bar` — location, time, mood, budget selectors
5. `.suggestions` — quick-prompt buttons
6. `#chat` — scrollable message thread
7. `.input-row` — textarea + send button
8. `<script>` — all JavaScript (API config, state, event handlers, DOM helpers)

## JavaScript Structure (inside `<script>`)
- **Constants**: `API_URL`, `SYSTEM_PROMPT`
- **State**: `conversationHistory` array
- **Functions**:
  - `getContext()` — reads current selector values
  - `quickAsk(text)` — fills input and triggers send
  - `sendMessage()` — main handler; builds message, calls API, renders response
  - `addMessage(role, text)` — creates and appends a chat bubble to DOM
  - `formatText(text)` — converts markdown-lite syntax to HTML
  - `showTyping()` / `removeTyping(id)` — typing indicator lifecycle
- **Init**: Auto-sets time-of-day selector based on `new Date().getHours()`

## Conventions
- All styling via CSS custom properties — add new tokens to `:root` before using them
- New UI sections follow the existing pattern: semantic HTML element + BEM-like class names
- Keep JS functions small and single-purpose
- Any new context selectors should follow the `.ctx-chip > select` pattern and be read inside `getContext()`
- Suggested prompts use `onclick="quickAsk('...')"` inline handlers to match existing style
