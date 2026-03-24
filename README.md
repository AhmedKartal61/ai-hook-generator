# AI Hook Generator

A single-file web app that generates 10 high-converting content hooks using the Claude API. Enter your niche, audience, and pain point — get 10 distinct hook angles in seconds.

---

## Prerequisites

You need an **Anthropic API key** to use this app.

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign up or log in
3. Navigate to **API Keys** → **Create Key**
4. Copy the key (it starts with `sk-ant-...`)

The app uses `claude-haiku-4-5-20251001` — the fastest and cheapest Claude model. Generating 10 hooks costs less than $0.01 per run.

---

## Running Locally

### Method 1: Open directly in browser (simplest)

1. Double-click `index.html` or drag it into your browser
2. Enter your API key in the app
3. Fill in your niche, audience, and pain point
4. Click **Generate**

> **Note:** If you see a CORS error when clicking Generate, use Method 2 instead. Some browsers block API calls from `file://` URLs.

### Method 2: Local HTTP server (recommended)

This avoids any potential CORS issues by serving the file over HTTP.

**If you have Python installed:**
```bash
cd outputs/ai-hook-generator
python3 -m http.server 8080
```
Then open `http://localhost:8080` in your browser.

**If you have Node.js installed:**
```bash
npx serve outputs/ai-hook-generator
```
Then open the URL it shows (usually `http://localhost:3000`).

---

## Deploying Online (Free)

### Option A: Netlify (easiest — drag and drop)

1. Go to [app.netlify.com](https://app.netlify.com) and sign up (free)
2. On the dashboard, find the **"Deploy manually"** box at the bottom
3. Drag the `outputs/ai-hook-generator/` folder into the box
4. Netlify instantly gives you a public URL like `https://random-name-123.netlify.app`
5. Share that link with anyone

To update the app: drag the folder again — Netlify replaces the deployment.

**Optional: Custom subdomain**
In Site Settings → Domain Management → you can rename it to `your-app-name.netlify.app` for free.

---

### Option B: GitHub Pages

1. Create a new GitHub repository (can be private or public)
2. Upload `index.html` to the repo (you can do this via the GitHub web UI)
3. Go to **Settings → Pages**
4. Under **Source**, select `main` branch and `/ (root)` folder
5. Click **Save**
6. GitHub gives you a URL like `https://yourusername.github.io/repo-name`

> If you put `index.html` in a subfolder, set the Pages source to that folder.

---

## How It Works

1. You enter your Anthropic API key (stored in your browser's `localStorage` — never sent anywhere except Anthropic's API)
2. When you click Generate, the app sends a request directly from your browser to `https://api.anthropic.com/v1/messages`
3. Claude generates 10 hooks using 10 different copywriting frameworks (Bold Claim, Curiosity Gap, Story opener, etc.)
4. The hooks appear with copy buttons for easy use

---

## Customising the Hooks

To change the hook frameworks or prompt, open `index.html` in a text editor and find the `buildPrompt()` function in the `<script>` section. Edit the list of frameworks or the instructions to Claude to customise output style.

To change the AI model, find `'claude-haiku-4-5-20251001'` in the script and replace it with another model (e.g. `claude-sonnet-4-6` for higher quality at higher cost).

---

## Troubleshooting

| Issue | Fix |
| --- | --- |
| CORS error | Use Method 2 (local server) or deploy to Netlify/GitHub Pages |
| 401 Unauthorized | API key is invalid or expired — generate a new one at console.anthropic.com |
| 429 Too Many Requests | You've hit your rate limit — wait a moment and retry |
| Hooks look generic | Be more specific with your audience and pain point inputs |
