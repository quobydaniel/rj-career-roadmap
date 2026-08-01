---
created: 2026-07-31
type: master-guide
status: active
tags: [career, saudi-job, github, linkedin, freelance, dual-purpose]
---

# 🏗️ The Career Stack — One Action, Three Returns

> **The core idea:** Every Door 1 action (building a dashboard, pitching a client, delivering a report) doesn't just earn GHS 200. It ALSO builds your GitHub, LinkedIn, freelance profile, and Saudi job portfolio — simultaneously, for free.
> This is how a broke person builds a career while surviving. You don't have time to do them separately. So we make every action count triple.
> See also: [[RJ Master Plan — One Rep a Day]] · [[How to Find Clients — Door 1]]

---

## 🧠 The Dual-Purpose Mindset (memorize this)

```
OLD WAY:  Build dashboard → deliver → get paid → forget about it
                    ↓
NEW WAY:  Build dashboard → deliver → get paid
                ↓                         ↓
          Put code+data on GitHub    Write a LinkedIn post about it
                ↓                         ↓
          Portfolio repo grows        Saudi recruiters see activity
                ↓                         ↓
          Freelance profile gets      "Google Data Analytics cert + real
          a portfolio piece           client work in Accra"
```

**One dashboard = 3 returns:**
1. GHS 200 (rent)
2. 1 GitHub commit + repo (portfolio)
3. 1 LinkedIn post + project entry (recruiter bait)

Every. Single. Time.

---

## 📋 THE 4-PORTFOLIO STACK you're building (in parallel with Door 1)

### Stack 1 — GitHub (your proof you can code/analyze)
**Goal:** 3 public repos with clean READMEs by end of Door 2 (week 8).
**Starts:** NOW, in Door 1, with your first real client dashboard.

### Stack 2 — LinkedIn (your recruiter-facing profile)
**Goal:** All-Star profile + 10 posts + 50 connections by end of Door 2.
**Starts:** NOW, with one post about your first client dashboard.

### Stack 3 — Freelance profile (Upwork/Fiverr — slow burn)
**Goal:** Profile live + 3 portfolio pieces by Door 2 end.
**Starts:** After Door 1 (week 3) — don't split focus now. But prep the material.

### Stack 4 — Portfolio website (upsideonly.com + quoby-rj-portfolio)
**Goal:** Live site hosting your 3 projects by Door 3.
**Starts:** Door 2 (week 7–8), using the React/Vite site you already built.

---

## 🔧 SETUP CHECKLIST — do these in Door 1 (setup, not procrastination)

These are 30-minute one-time setups, not endless projects. Do them once, they compound forever.

### A. Git identity (2 min — do this TODAY)
Without this, you can't commit anything to GitHub. Run in terminal:
```bash
git config --global user.name "RJ Quoby"
git config --global user.email "your-gmail@gmail.com"
git config --global init.defaultBranch main
```

### B. GitHub account + CLI (15 min — do this in the next 2 days)
1. Create a GitHub account at github.com (if you don't have one — use your Gmail)
2. Install the GitHub CLI on Ubuntu:
   ```bash
   sudo apt install -y gh
   ```
3. Authenticate:
   ```bash
   gh auth login
   ```
   (Follow prompts → GitHub.com → HTTPS → login with browser)
4. Verify:
   ```bash
   gh auth status
   ```

### C. LinkedIn profile — upgrade to "All-Star" (30 min — do this this week)
Every section matters for Saudi recruiters searching "Data Analyst Ghana" or "Data Analyst Saudi Arabia":

| Section | What to write |
|---|---|
| **Headline** | "Data Analyst \| Google Certified \| Helping small businesses turn raw data into decisions — available for Saudi Arabia & remote" |
| **About** | 3 paragraphs: (1) Who you are + Google cert, (2) What you do — dashboards, data cleaning, analytics, (3) What you're looking for — data analyst role in Saudi/remote. Mention XAUUSD + Aramco analysis as interests. |
| **Experience** | Add "Freelance Data Analyst — Accra, Ghana (2026–present)" — you ARE one the moment you get your first client. |
| **Education** | Google Data Analytics Certificate + any other courses. |
| **Skills** | Data Analysis, SQL (basic), Excel/Google Sheets, Python (basic), Data Visualization, Dashboards, Business Analytics |
| **Featured** | Add your dashboard screenshots as you build them. |

### D. GitHub repos — the 3 you'll build (in order)

| Repo | Built when | What it proves |
|---|---|---|
| `sales-dashboard-templates` | Door 1 (NOW) | That you can build real client dashboards. Each client = a subfolder. |
| `xauusd-backtest-report` | Door 2 (weeks 3–4) | That you can do financial data analysis (Python + pandas + matplotlib). |
| `aramco-safety-analysis` | Door 2 (weeks 5–6) | That you understand Saudi-relevant industrial data. Your golden ticket. |

---

## 📐 THE DUAL-PURPOSE WORKFLOW — do this for EVERY client

When you get a client (say, "Kofi Pharmacy"), you don't just deliver the dashboard. You run this 5-step workflow:

### Step 1 — Build (the skill rep)
Build their dashboard in LibreOffice Calc / Google Sheets. Deliver. Get paid.

### Step 2 — Generalize (anonymize the data)
- Copy the workbook. Replace their real business name with "Client A — Pharmacy"
- Replace real product names with generic ones ("Product 1", "Product 2")
- Replace real prices with round numbers
- **Never put a client's real numbers on GitHub or LinkedIn.** This is non-negotiable privacy.

### Step 3 — Push to GitHub (the portfolio rep)
```bash
cd ~/Projects/Finance\ &\ Data/sales-dashboard-templates
mkdir kofi-pharmacy-anon
# copy the anonymized workbook + a README.md here
git add .
git commit -m "Add pharmacy sales dashboard — EMA 21/50 analysis methodology"
git push
```
**Every repo MUST have a great README.md.** Template:
```markdown
# Sales Dashboard Template — Pharmacy

## What it does
One-page dashboard showing top products by revenue, profit margins, category breakdown.

## Tools used
- LibreOffice Calc / Google Sheets
- Formulas: SUMIF, QUERY, pivot tables
- Output: printable PDF dashboard

## Methodology
1. Import raw sales CSV
2. Calculate revenue (qty × price), profit, margin
3. Aggregate by product and category
4. Visualize with bar chart + pie chart
5. Assemble one-page printable report

## Sample output
(attach a PDF screenshot here)
```

### Step 4 — Post on LinkedIn (the recruiter rep)
Write a 3-4 line post (takes 5 min):
> "Just delivered my first client dashboard 📊
> A pharmacy in Accra came to me with 60 rows of raw sales data in a notebook.
> I cleaned it, calculated profit margins, and built a one-page dashboard showing their top products and where money leaks.
> Data analytics isn't theory — it's turning chaos into clarity.
> #DataAnalytics #GoogleCertified #Accra #OpenToWork"

Attach the anonymized screenshot. Tags: `#DataAnalytics #OpenToWork #SaudiArabia #Ghana`

### Step 5 — Add to freelance profile (the rep that pays later)
When you create your Upwork/Fiverr in Door 2, you'll have REAL portfolio pieces to show.

---

## 🎯 THE SAUDI JOB — what you're really building toward

Saudi employers (aramco, SABIC, STC, banks, healthcare) hire data analysts who can show:
1. **Real delivered work** — your GitHub repos
2. **Professional presence** — your LinkedIn
3. **Saudi-relevant experience** — your Aramco safety analysis (Door 2 project)
4. **A cert** — you already have the Google one ✅
5. **Communication ability** — your LinkedIn posts prove you can write in English

### The Saudi application path (Door 3, week 9+)
| Platform | How to use |
|---|---|
| **Bayt.com** | Create profile, upload CV, search "Data Analyst Saudi Arabia" |
| **GulfTalent** | Same — biggest Gulf-focused job board |
| **Naukri Gulf** | Strong for Indian/Ghanaian expats in KSA |
| **LinkedIn Jobs** | Search "Data Analyst Riyadh/Jeddah/Dammam", filter to Saudi, set alerts |
| **Company career pages** | aramco.com/careers, sabic.com, stc.com.sa — apply directly |
| **Recruitment agencies** | Michael Page Saudi, Hays Gulf — reach out on LinkedIn |

### What a Saudi data analyst needs (and how you'll have it)
| Requirement | How you get it | When |
|---|---|---|
| Data analysis skill | Door 1 (dashboards) + Door 2 (XAUUSD + Aramco projects) | Week 8 |
| Portfolio | Your 3 GitHub repos + upsideonly.com live | Week 8 |
| Professional English | LinkedIn posts + CV + cover letters | Ongoing |
| Saudi-relevant industry knowledge | Aramco safety analysis project | Week 6 |
| SQL (often required) | Learn basics in Door 2 (free — Khan Academy / SQLBolt) | Week 8 |
| Python/pandas (bonus) | From your XAUUSD backtest project | Week 4 |

---

## 📅 WEEKLY DUAL-PURPOSE CHECKLIST — pin this

Every week, do at minimum:

- [ ] **2 GitHub commits** (from client work or practice)
- [ ] **1 LinkedIn post** (about a build, a client, a learning, a chart)
- [ ] **5 LinkedIn connection requests** (to data analysts in Saudi/Gulf)
- [ ] **1 CV update** (add that week's work to Experience section)
- [ ] **1 README written** (for any repo you touched that week)

That's 5 small actions per week. Each takes 5–15 min. Each compounds.

---

## ⚠️ THE TRAP TO AVOID — read when tempted

**You will be tempted to "build the GitHub portfolio first, THEN start Door 1."** Don't.
The dual-purpose system only works if you build REAL client work. Fake practice dashboards don't land jobs. Real delivered work does.
- Door 1 builds the GitHub, not the other way around.
- The client comes first. The GitHub is the *exhaust* of the client work. Not the engine.

**You'll also be tempted to spend 3 hours on your LinkedIn profile before you have any work to show.** Don't. A LinkedIn with no work is an empty shop. A LinkedIn with 1 real dashboard screenshot is a shop with one product. Add products (work) first, polish the shop later.

---

## 🚦 RIGHT NOW — what to actually do today

### Today (30 min total):
1. Run the git config commands above (2 min)
2. If you have a GitHub account, install `gh` CLI (`sudo apt install -y gh`) and `gh auth login` (15 min)
3. Create the repo structure:
   ```bash
   cd ~/Projects/Finance\ \&\ Data
   mkdir sales-dashboard-templates
   cd sales-dashboard-templates
   git init
   echo "# Sales Dashboard Templates — Real client dashboards (anonymized)" > README.md
   git add .
   git commit -m "Initial commit"
   ```
4. Update your LinkedIn headline to the one above (5 min)

### This week (as you get clients):
- Each client dashboard → anonymize → push to `sales-dashboard-templates` repo → LinkedIn post
- That's the cycle. Repeat 2–3 times in Door 1. You'll have a real portfolio by week 2.

---

## ✅ WHAT YOU'LL HAVE BY END OF DOOR 1 (week 2)

| Asset | Where | Result |
|---|---|---|
| 2–3 client dashboards delivered | Real businesses in Accra | GHS 500+ earned, rent paid |
| 1 active GitHub repo | `sales-dashboard-templates` | 2–3 commits, clean READMEs |
| LinkedIn profile | 2–3 posts, "Freelance Data Analyst" in Experience | Recruiter-visible |
| 1 portfolio screenshot | From your best client dashboard | Goes on LinkedIn + future upsideonly.com |

**That's not just rent paid. That's the foundation of a career handed to a Saudi recruiter in week 9.**

---

*Last updated: 2026-07-31*
*Every Door 1 walk-in feeds four stacks: cash, GitHub, LinkedIn, freelance. One action, triple return.*
