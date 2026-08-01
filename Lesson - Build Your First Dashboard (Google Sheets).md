---
created: 2026-07-31
type: lesson
status: active
tags: [learning, dashboard, google-sheets, practical-skills]
---

# 🎓 Lesson: Build Your First Dashboard in Google Sheets

> **Goal:** Learn the analytics workflow by building one real, printable dashboard.
> **Tool:** Google Sheets (free, browser-based, opens in Firefox).
> **Time:** 60–90 minutes the first time. You'll do it in 20 after the 3rd time.
> **Why this matters:** This is the EXACT thing you're selling in Door 1. After today you'll know how it works — and you can build a client's version in an evening. Earn while you learn.
> See also: [[Door 1 — First Pitch (held by hand)]] · [[RJ Master Plan — One Rep a Day]]

---

## 📚 The 6 Steps Every Dashboard Needs

Every dashboard — for any client, in any tool — follows these 6 steps. Memorize them:

1. **The Question** — what is the dashboard trying to answer?
2. **The Raw Data** — what data do you have?
3. **Clean + Calculate** — add columns the data doesn't have yet (e.g., profit)
4. **Aggregate** — group rows into summaries (top products, totals)
5. **Visualize** — turn tables into charts
6. **Assemble** — put it on one page, make it look professional, print

That's it. Everything in data analytics is one of these 6 steps. Today we do all 6.

---

## 🔧 SETUP (2 minutes)

1. **Open Firefox** → go to **`sheets.google.com`**
2. Sign in with a Gmail account. (If you don't have one, stop here and tell me — I'll give you an offline alternative.)
3. Click **"Blank"** (the `+` icon) → a new spreadsheet opens.
4. Rename it (top-left) → **"ABC Pharmacy Dashboard — lesson 1"**.
5. In a new browser tab, open the raw data file: `Roadmap/Phase 0 - Raw Sales Data.csv`. You'll see 60 rows of CSV text.

---

## 🟢 STEP 1 — The Question (5 min)

Before touching any data, write the question the dashboard answers.

In **cell A1**, type:

```
ABC PHARMACY — SALES DASHBOARD (July 2026)
```

In **cell A2**, type the question it answers:

```
Question: Which products should I restock first, and where is money leaking?
```

**Why this step matters (and you'll be asked it):** A client will say "what do I actually GET for my GHS 200?" Your answer is one sentence:
> *"A one-page report telling you what's selling best, what's making you money, and what to restock first — so you stop buying things that don't sell."*

That sentence IS the product. Dashboards answer questions. No question = no dashboard.

---

## 🟢 STEP 2 — Get the Raw Data In (5 min)

Two ways:

### Easy way (recommended):
1. In Firefox, open `Roadmap/Phase 0 - Raw Sales Data.csv` (double-click in your file manager).
2. Select ALL the text (Ctrl+A in your text editor), copy (Ctrl+C).
3. In Google Sheets, click **cell A4**, paste (Ctrl+V).
4. The text will spread across columns A, B, C, D, E, F.

### Proper way (do this — it's cleaner):
1. In Sheets, go to top menu: **File → Import → Upload**.
2. Drag `Phase 0 - Raw Sales Data.csv` into the box.
3. Choose **"Insert new sheet"** and **"Separator type: Comma"**.
4. Click **Import** → a new sheet appears with clean table data + headers (row 1).

**Your raw data should have these 6 columns:**
`date` | `item` | `category` | `qty` | `unit_price` | `cost_per_unit`

**What to notice (this is the lesson):** Real client data is MESSY. It might have typos, missing columns, weird formatting. This is what you'll see when a client hands you their notebook or Excel. Your job = clean it. Today ours is clean. Tomorrow's client's won't be.

---

## 🟢 STEP 3 — Clean + Calculate (10 min)

The raw data has `qty`, `unit_price`, and `cost_per_unit` — but NO revenue and NO profit. The client never tracks these. YOUR VALUE = calculating them. This is the core skill.

### Add a "revenue" column:
1. In your imported sheet, click column **G** (the first empty column).
2. In cell `G1`, type: `revenue`
3. In cell `G2`, type this formula:
   ```
   =D2*E2
   ```
   (qty × unit_price = revenue — that's what this column means)
4. Press **Enter**. You'll see the total for row 2.
5. Now the magic: click cell `G2` again. See the small blue square in the bottom-right corner? **Double-click it.** The formula fills all the way down to the last row. (60 rows done in 1 second. This is what analysts do all day.)

### Add a "profit" column:
1. Click column **H**. Cell `H1` → type `profit`
2. Cell `H2` → type:
   ```
   =D2*(E2-F2)
   ```
   (qty × (price − cost) = profit)
3. Double-click the blue square → fill down.

### Add a "profit_margin" column (%):
1. Column I → `I1` → `profit_margin`
2. `I2` →
   ```
   =H2/G2
   ```
3. Fill down.
4. Select column I → top menu **Format → Number → Percent**. Now it shows `53%` instead of `0.53`.

**CONGRATULATIONS.** You just did the most important skill in data analytics: **turning raw rows into calculated columns.** You now have 9 columns instead of 6. The client gave you 6 — you added 3 that mean something. THAT's the value they pay for.

---

## 🟢 STEP 4 — Aggregate (10 min)

Now you have 60 rows of sales. A client can't read 60 rows. You need to **summarize** them: per product, per category, and totals.

### Build the "Top Products" table:
1. Click the `+` at the bottom of Sheets to add a **new sheet** (call it "Dashboard").
2. In the new sheet, cell `A3` → type: `TOP PRODUCTS BY REVENUE`
3. Row 4: `Product` | `Qty Sold` | `Revenue (GHS)` | `Profit (GHS)` | `Margin %`

Now the powerful part — use `QUERY` (Google Sheets' secret weapon for analysts):

4. In cell `A5`, paste this formula:
   ```
   =QUERY('Phase 0 - Raw Sales Data'!A:I,
   "SELECT B, SUM(D), SUM(G), SUM(H), SUM(H)/SUM(G)
    WHERE B IS NOT NULL
    GROUP BY B
    ORDER BY SUM(G) DESC
    LABEL SUM(D) 'Qty', SUM(G) 'Revenue', SUM(H) 'Profit', SUM(H)/SUM(G) 'Margin'
    FORMAT SUM(H)/SUM(G) '0%' ", 0)
   ```

**What this formula does (read it line by line — this is the lesson):**
- `SELECT B` → give me the item name (column B)
- `SUM(D)` → sum of quantity (total sold per item)
- `SUM(G)` → sum of revenue
- `SUM(H)` → sum of profit
- `SUM(H)/SUM(G)` → profit margin = profit ÷ revenue
- `GROUP BY B` → group all rows by item (collapse the 60 rows into one row per product)
- `ORDER BY SUM(G) DESC` → sort by revenue, biggest first
- `LABEL` → rename the calculated columns (so they print nicely)
- `FORMAT SUM(H)/SUM(G) '0%'` → show the margin as a percentage

Press Enter. Your top-products table appears instantly, sorted by revenue. **That's a real analytics technique in one formula.** This is what you'd charge GHS 200 for.

### Build a "Category" table:
Same idea, but group by category. In cell `A20`:
```
=QUERY('Phase 0 - Raw Sales Data'!A:I,
"SELECT C, SUM(D), SUM(G), SUM(H)
 WHERE C IS NOT NULL
 GROUP BY C
 ORDER BY SUM(G) DESC
 LABEL SUM(D) 'Qty', SUM(G) 'Revenue', SUM(H) 'Profit' ", 0)
```

### Build totals:
In a clean area (cell `G3`):
```
="Total Revenue: GHS " & ROUND(SUM('Phase 0 - Raw Sales Data'!G:G),0)
```
In `G4`:
```
="Total Profit: GHS " & ROUND(SUM('Phase 0 - Raw Sales Data'!H:H),0)
```

---

## 🟢 STEP 5 — Visualize (10 min)

Tables are good. Charts sell. Let's build 2 charts.

### Chart 1 — Top 5 products by revenue (bar chart)
1. Select the top-products table you just built — say rows 5 to 10, columns A to D.
2. Top menu: **Insert → Chart**. A chart panel opens on the right.
3. Chart type → **"Column chart"** (vertical bars).
4. X-axis → your product names. Series → Revenue.
5. Title it: **"Top 5 Products by Revenue"**.
6. Move it to a corner of your Dashboard sheet.
7. (If it looks wrong, don't panic — just drag the chart data range in the panel to cover the right cells.)

### Chart 2 — Revenue by category (pie or donut)
1. Select the category table.
2. Insert → Chart → **"Pie chart"**.
3. Title: **"Revenue by Category"**.
4. Move under Chart 1.

---

## 🟢 STEP 6 — Assemble + Print (10 min)

### Layout (your "Dashboard" sheet):
- A1 → big title: **"ABC PHARMACY — SALES DASHBOARD (July 2026)"**
- A2 → the question: *"Question: Which products should I restock first, and where is money leaking?"*
- A3 → "TOP PRODUCTS BY REVENUE" (your QUERY table below)
- (Chart 1 on the right of the table)
- A20 → "REVENUE BY CATEGORY" (your category table)
- (Chart 2 below it)
- Right side or bottom → the totals (Total Revenue, Total Profit)
- A blank cell at the bottom → **"Key insight: Your top 3 products make up most of your revenue. Never let them run out of stock."**

### Make it look professional:
1. Select row 1 → bold, font size 14.
2. Select the table headers (row 4) → bold, background fill light blue.
3. Select all currency cells → Format → Number → Currency (choose GHS or just decimal).
4. Freeze the header row: View → Freeze → 1 row.
5. Add borders to tables: select cells → borders icon → all borders.

### Print as PDF (so you can carry it):
1. Top menu: **File → Print** (or Ctrl+P).
2. In the print dialog:
   - **Destination:** Save as PDF
   - **Layout:** Landscape
   - **Scale:** Fit to page width
   - **Margins:** Minimum
3. Click **Save** → save the PDF to `Downloads/ABC Pharmacy Dashboard.pdf`.
4. Send that PDF to your phone (WhatsApp yourself / Bluetooth / upload to Google Drive).
5. Tomorrow, go to ANY cafe/print shop → print the PDF (~GHS 2–5).

---

## 📝 What you actually LEARNED today (be proud of this)

By finishing this lesson, you now understand:

| Concept | You used it |
|---|---|
| Raw vs calculated data | You added revenue, profit, margin columns |
| A formula in a cell | `=D2*E2` |
| Auto-fill down a column | double-clicked the blue square |
| Number formatting (currency / %) | Format → Number |
| Grouping/aggregation | `QUERY` with `GROUP BY` |
| Sorting results | `ORDER BY ... DESC` |
| Charts from a table | Insert → Chart |
| One-page dashboard | Assembled tables + charts + totals |

**That's a real, working analytics vocabulary.** You're not "theoretically good" anymore. You can DO this.

---

## ✅ After this lesson — what changed

- You KNOW how a dashboard is built, end-to-end, in the tool you'd actually use with a client.
- You can repeat this for a real client's data in 30–60 minutes (you'll go from 90 min → 20 min by the 5th client).
- The `Roadmap/Sample Dashboard - ABC Pharmacy.xlsx` I built earlier now makes sense when you look at it — you can see exactly which columns created which cells.
- You can answer a client's question: *"How does this actually work?"* — by walking them through it on a phone screen.

---

## 🎯 Your move

After you finish this lesson, go back to [[Door 1 — First Pitch (held by hand)]] and execute tomorrow morning.

You're no longer "I don't know how to build." You're "I built one. I can build yours."

---

*Lesson date: 2026-07-31*
*Rep #1 in your analytics journey. Many more to come. One at a time.*
