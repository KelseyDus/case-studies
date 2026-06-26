# Oswald Marketing — Case Study Agent

Two files. No build step. Deploys to Vercel in under 5 minutes.

```
index.html        ← the whole app
api/generate.js   ← tiny server function that calls Anthropic (keeps your key secure)
```

---

## Deploy to Vercel

### 1. Get an Anthropic API key
[console.anthropic.com](https://console.anthropic.com) → API Keys → Create key. Copy it.

### 2. Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR-ORG/case-study-agent.git
git push -u origin main
```

### 3. Deploy on Vercel
1. [vercel.com](https://vercel.com) → **Add New Project** → import your repo
2. Under **Environment Variables** add:
   - Name: `ANTHROPIC_API_KEY`
   - Value: the key you copied in step 1
3. Click **Deploy**

Your app is live. Share the URL with your team.

---

## Why two files instead of one?

Anthropic's API blocks direct browser requests (CORS policy). The `api/generate.js` file runs on Vercel's servers, makes the API call there, and returns the result to the browser. Your API key never touches the browser — it stays secure on the server.

---

## Updating the app
Edit `index.html`, push to `main`, Vercel redeploys automatically.
