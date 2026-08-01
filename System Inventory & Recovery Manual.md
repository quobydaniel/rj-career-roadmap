---
created: 2026-08-01
type: master-inventory
status: active
tags: [inventory, backup, recovery, system-map]
---

# 🗂️ System Inventory & Recovery Manual

> **Purpose:** If you lose your laptop tomorrow, this single file tells you (or anyone) how to recreate your entire working system from scratch — every tool, every account, every file, every step.
> **Rule:** Every time you set up something new, add it here. This is your single source of truth.
> **Backup rule:** This file lives in your Obsidian vault AND syncs to cloud + mobile (see Backup Setup below). If the laptop dies, this file survives.

---

## 🧱 THE FULL SYSTEM — what you have, what each piece does

### 1. Your Knowledge Base (Obsidian Vault)
- **App:** Obsidian (snap install on Ubuntu)
- **Vault location:** `~/Desktop/My_Vault/`
- **Contents:** Roadmap folder (plans, lessons, trackers), Projects folder, an empty vault file
- **If lost:** Reinstall Obsidian → re-download vault from Google Drive backup (see Backup Setup)

### 2. Your Spreadsheet Tool
- **App:** LibreOffice Calc (apt install)
- **Native format:** `.ods` (LibreOffice Calc Spreadsheet)
- **Also opens:** `.xlsx` (Excel), `.csv` (raw data)
- **If lost:** `sudo apt install -y libreoffice-calc`

### 3. Your Code / Version Control
- **Git identity:** `user.name = RJ Quoby`, `user.email = your-gmail@gmail.com`, `init.defaultBranch = main`
- **GitHub CLI:** `gh` (apt install) — authenticate with `gh auth login`
- **Projects folder:** `~/Projects/` (organized by category per AGENTS.md)
- **If lost:** Run the git config commands + `sudo apt install -y gh` + `gh auth login`

### 4. Your Obsidian MCP Connection
- **MCP server type:** obsidian-mcp (npm) OR Obsidian Local REST API plugin (current)
- **Obsidian plugin:** Local REST API community plugin → enabled → port 27124 → https
- **ZCode config:** `~/.zcode/cli/config.json` → `mcp.servers.obsidian` → `{"type":"http", "url":"https://127.0.0.1:27124/mcp/", "headers":{"Authorization":"Bearer <token>"}}`
- **If lost:** See "Recreating the Obsidian MCP" section at the bottom of this doc

### 5. Your Browser
- **App:** Firefox (installed by default on Ubuntu)
- **Used for:** Google Sheets (sheets.google.com), LinkedIn, GitHub, WhatsApp Web, printing support PDFs

### 6. Your Work Files (the actual sellable stuff)
All in `~/Desktop/My_Vault/Roadmap/`:
- `RJ Master Plan — One Rep a Day.md` — the 3-door strategy
- `Career Stack — One Action, Three Returns.md` — how Door 1 feeds Saudi job + GitHub + LinkedIn
- `Fire Drill Tracker.md` — daily scoreboard
- `Pitch Script.md` — what to say in shops
- `Door 1 — First Pitch (held by hand).md` — Day-1 minute-by-minute
- `How to Find Clients — Door 1.md` — where to walk, who to target
- `Lesson - Build Your First Dashboard (Google Sheets).md` — the skill lesson
- `Phase 0 - Raw Sales Data.csv` — practice data
- `Sample Dashboard - ABC Pharmacy.xlsx` — pre-built sample (data layer only, no charts)
- `My First Dashboard.ods` — YOUR build (in progress)
- `Idea Vault — Parked Ideas.md` — where Bacopa/Jarvis/etc. wait

### 7. Your Accounts (online)
- **Gmail:** (your email — record it here: ____________________)
- **GitHub:** (your username — record it here: ____________________)
- **LinkedIn:** (your profile URL — record it here: ____________________)
- **WhatsApp:** (your number — record it here: ____________________)
- **GitHub CLI auth:** `gh auth login` via browser

---

## ☁️ BACKUP SETUP — make your vault + work survive laptop loss

### Tier 1 — Google Drive sync (free, automatic, cloud + mobile access)
**One-time setup (10 minutes):**
1. Install Google Drive desktop sync for Linux — use `rclone` (free, works on Ubuntu):
   ```bash
   sudo apt install -y rclone
   rclone config
   # → n (new remote) → name it "gdrive" → choose "drive" (Google Drive)
   # → follow prompts → authenticate in browser
   # → leave root_folder_id blank → leave scope as default → done
   ```
2. Set up periodic sync of your vault to Google Drive:
   ```bash
   # Test once:
   rclone sync ~/Desktop/My_Vault gdrive:My_Vault_Backup --progress
   ```
3. Create a daily auto-sync cron job:
   ```bash
   crontab -e
   # Add this line (syncs every day at 11pm):
   0 23 * * * rclone sync /home/rj_quoby/Desktop/My_Vault gdrive:My_Vault_Backup --quiet
   ```
4. **Result:** Every night while you sleep, your entire vault uploads to Google Drive. Accessible from any browser, your phone, anywhere.

### Tier 2 — Git for the Roadmap folder (free, versioned, public portfolio)
Your vault doesn't need git. But your *Roadmap* should be its own git repo — versioned + pushed to GitHub. That way it's backed up AND it's a visible "work in progress" on your GitHub profile:

```bash
cd ~/Desktop/My_Vault/Roadmap
git init
echo "# RJ's Career Roadmap — Data Analytics journey from Accra to Saudi Arabia" > README.md
git add .
git commit -m "Initial commit — Door 1 fire drill setup"
# After GitHub CLI is installed:
gh repo create rj-roadmap --public --source=. --push
```

### Tier 3 — Manual phone copy (the bulletproof last resort)
Once a week, after Sunday review:
1. Zip the Roadmap folder: `cd ~/Desktop/My_Vault && zip -r Roadmap-$(date +%F).zip Roadmap`
2. WhatsApp it to yourself (or upload to Google Drive)
3. Now it's on your phone. Bulletproof.

---

## 📋 THE WEEKLY BACKUP CHECKLIST (Sundays, 5 min)

- [ ] Verify rclone ran: `rclone ls gdrive:My_Vault_Backup | tail -10` (should show your files)
- [ ] Git status on Roadmap repo: `cd ~/Desktop/My_Vault/Roadmap && git status` → commit any uncommitted docs
- [ ] Push to GitHub: `cd ~/Desktop/My_Vault/Roadmap && git push`
- [ ] Manually zip + send to phone (Tier 3)
- [ ] Verify phone received the zip
- [ ] Update this inventory file if anything changed this week

5 minutes a week. Full recovery insurance.

---

## 🔄 RECREATING THE SYSTEM FROM SCRATCH (if laptop is lost)

### Phase A — Fresh Ubuntu install (15 min):
```bash
# 1. Install Obsidian
sudo snap install obsidian --classic

# 2. Install LibreOffice Calc
sudo apt update && sudo apt install -y libreoffice-calc

# 3. Install git + GitHub CLI
sudo apt install -y git gh

# 4. Configure git identity
git config --global user.name "RJ Quoby"
git config --global user.email "your-gmail@gmail.com"
git config --global init.defaultBranch main

# 5. Authenticate GitHub
gh auth login
```

### Phase B — Restore your Obsidian vault (10 min):
1. Open browser → Google Drive → `My_Vault_Backup`
2. Download the whole folder as a zip
3. Unzip to: `~/Desktop/My_Vault`
4. Open Obsidian → "Open folder as vault" → select `~/Desktop/My_Vault`
5. All your notes, trackers, lessons, roadmap → restored

### Phase C — Recreate the Obsidian MCP (10 min, optional):
1. Open Obsidian → Settings (gear icon bottom-left) → Community plugins
2. Browse → search "Local REST API" → Install → Enable
3. Open the plugin settings → copy the API key (Bearer token)
4. Note the port (default 27124) → ensure "HTTPS" is on
5. Edit `~/.zcode/cli/config.json` → add this block:
   ```json
   "mcp": {
     "servers": {
       "obsidian": {
         "type": "http",
         "url": "https://127.0.0.1:27124/mcp/",
         "headers": { "Authorization": "Bearer <PASTE_YOUR_NEW_TOKEN>" },
         "enabled": true,
         "timeoutMs": 30000
       }
     }
   }
   ```
6. Restart ZCode

### Phase D — Restore your repos (per repo):
```bash
# For each repo you had (sales-dashboard-templates, xauusd-backtest, etc):
gh repo clone <your-username>/<repo-name>
```

### Phase E — Restore your working files:
Your Roadmap + roadmap docs are already restored via the vault (Phase B).
Your projects are restored via GitHub (Phase D).
You're operational again in under 1 hour.

---

## 📦 THE COMPLETE FILE INVENTORY (so you know what you have)

### Obsidian Vault (`~/Desktop/My_Vault/`)
| File/Folder | Last status | Purpose |
|---|---|---|
| `Roadmap/RJ Master Plan — One Rep a Day.md` | Active | The 3-door strategy |
| `Roadmap/Career Stack — One Action, Three Returns.md` | Active | How Door 1 → Saudi job |
| `Roadmap/Fire Drill Tracker.md` | Active | Daily scoreboard |
| `Roadmap/Pitch Script.md` | Active | What to say in shops |
| `Roadmap/Door 1 — First Pitch (held by hand).md` | Active | Day-1 minute-by-minute |
| `Roadmap/How to Find Clients — Door 1.md` | Active | Where to walk, who to target |
| `Roadmap/Lesson - Build Your First Dashboard (Google Sheets).md` | Active | Skill lesson |
| `Roadmap/Phase 0 - Raw Sales Data.csv` | Static | Practice data (60 rows) |
| `Roadmap/Sample Dashboard - ABC Pharmacy.xlsx` | Static | Pre-built sample |
| `Roadmap/My First Dashboard.ods` | In progress | YOUR build |
| `Roadmap/Idea Vault — Parked Ideas.md` | Active | Bacopa/Jarvis parking |
| `Projects/` | Existing | Old Obsidian projects (AuTrader, BASIC, etc) |

### Projects Folder (`~/Projects/`)
Worth recovering via GitHub (most have .git folders):
- `Finance & Data/` — data-analytics repo, xauusd_1h.py (Door 2 material)
- `Web Development/quoby-rj-portfolio` — your portfolio site (Door 3 material)
- `Web Development/xaussd` — XAUUSD project (Door 2)
- `Automation & AI/youtube-automation` — future YouTube (Door 3)
- `Automation & AI/n8n` — n8n stuff
- ~30 other projects (Archive/legacy)

### Documents Folder (`~/Documents/`)
- `aramco-safety.md` — your Saudi-relevant industrial analysis (Door 2 GOLD)

### ZCode Config (`~/.zcode/cli/config.json`)
- Obsidian MCP server config
- Plugin enable/disable list

---

## 🔑 KEYS, TOKENS, PASSWORDS (record these — but don't commit to GitHub)

> ⚠️ NEVER commit real passwords/tokens to git. Store these in a password manager (Bitwarden free) or in an encrypted note + memorized. Only placeholders belong in this doc.

- [ ] Gmail password — [record in Bitwarden, not here]
- [ ] GitHub password — [record in Bitwarden, not here]
- [ ] Obsidian Local REST API Bearer token — [record in Bitwarden, not here]
- [ ] Laptop password — [memorize, don't write down]
- [ ] Google Drive rclone token — [stored by rclone config]

**Recommended:** Install Bitwarden free extension on Firefox → save every password there. The only thing you memorize is the master password. Everything else recovers from Bitwarden on any device.

---

*Last updated: 2026-08-01*
*Update this file every Sunday during your weekly review. It's your lifeboat.*
