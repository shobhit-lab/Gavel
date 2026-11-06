# ⚖️ Gavel: AI Code Review That Proves Its Claims

### 🏆 Flip the Switch Hackathon · Powered by Switch AI

> Every AI reviewer *claims* things. Gavel makes them **prove it**.
> Claims are verified in a sandbox, cross-examined, and escalated to a human, who has the final say. The ruling is then recorded as an ADR.

🔗 **Live demo:** <!-- paste your deployed link below -->
**https://gavel-weld.vercel.app/**

---

## 📖 What is Gavel?

Gavel turns every email, form, or ticket into a live **incident room**. AI agents gather context, assess severity, and draft the fix in minutes, and **your team makes the final call**.

Click **“Open a War Room!”** on the site to watch a full replay of a real review run (seeded PR `acme/shop#42`), captured from the Switch AI review backend:

```
gateway → room → claims → sandbox verification → cross-examination
        → escalation → human ruling → ADR
```

| Stage | What happens |
|---|---|
| **Trigger** | An email, form, or ticket opens a dedicated room. |
| **Context** | Agents gather severity, history, and a draft fix. |
| **Verify** | Each claim is tested in a sandbox instead of being taken on trust. |
| **Cross-examine** | Agents challenge each other's claims. |
| **Control** | Humans approve; Scribe records the decision as an ADR. |

---

## 🗂️ Project structure

```
.
├── index.html                # Landing page + War Room entry point
├── assets/
│   ├── warroom/warroom.js    # War Room replay (self-contained overlay)
│   ├── js/                   # Framer runtime bundles
│   ├── images/  fonts/       # Static media
│   └── brand/                # Favicons + OG image
├── package.json              # `npm start` / `npm run preview`
└── asset-map.json            # Original → local asset mapping
```

It's a **100% static site**: no build step, no backend, no API keys, no environment variables. The War Room is a recorded replay, so it behaves identically on your machine and in production.

---

## 💻 Run locally

> ⚠️ Serve the folder over HTTP rather than double-clicking `index.html`. The site loads ES modules, which browsers block on `file://`.

Pick **any one** of these:

**Option A: Python (nothing to install)**
```bash
python3 -m http.server 3000
```

**Option B: VS Code**
Install the *Live Server* extension → right-click `index.html` → **Open with Live Server**.

Then open **http://localhost:3000** (or the port your server prints) and click **Open a War Room!**.


---

## 🚀 Deploy

Because it's static, it deploys anywhere with zero configuration.

**Vercel (what we use)**
```bash
npm i -g vercel
vercel --prod
```
When prompted, accept the defaults: **Framework: Other**, **Build command: none**, **Output directory: `./`**.

**Netlify / Cloudflare Pages / GitHub Pages**
Drag and drop the folder, or point the host at the repo root. There is no build command and the publish directory is `/`.

> After redeploying, hard-refresh (**Ctrl/Cmd + Shift + R**) so your browser doesn't show a cached tab title or script.

---

## ✅ Local vs. deployed

| | Local | Deployed |
|---|---|---|
| Needs a build | ❌ | ❌ |
| Needs API keys / env vars | ❌ | ❌ |
| Needs internet | Only for Google resources if any | ✅ |
| War Room works | ✅ | ✅ |

---

## 🛠️ Troubleshooting

- **Blank page / console errors about modules:** you opened the file directly. Use one of the local server options above.
- **Old title or content after deploying:** hard-refresh, or clear the site cache.
- **Port already in use:** `npx serve . -l 4000` (or change the port in the Python command).

---

## 🤝 Credits

Built for the **Flip the Switch Hackathon**, powered by **Switch AI**.
Landing page built in Framer and exported as static HTML.
