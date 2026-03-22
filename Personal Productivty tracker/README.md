# 🧠 Daily Productivity Tracker (n8n + Sheets + Telegram)

I used to end my days thinking:

> “I was busy… but did I actually move forward?”

That question led me to build this **automated daily tracker** using **n8n**, **Google Sheets**, and a touch of **AI** magic.

---

## ⚙️ What This Workflow Does

This automation helps you **analyze how you spend every 15 minutes** of your day — automatically.

1. **Quarter-hour tracking**  
   Every 15 minutes, n8n checks your Google Sheet for time blocks.

2. **Smart categorization**  
   Each entry is labeled as:

   - ✅ **Productive** (deep work, client tasks, progress work)
   - 🌀 **Wasted** (scrolling, random clicks, distractions)
   - 🤔 **Unknown** (missing or vague entries)

3. **End-of-day summary**  
   At night, n8n sends a **clean Telegram report** — no fluff, just facts.  
   It highlights where your time went and what needs improvement.

---

## 📂 Files Included

- `daily-productivity-tracker.json` — n8n workflow file
- `sample_sheets.xlsx` — Google Sheets structure template (required)

> ⚠️ **Important:**  
> The attached `.xlsx` file defines the exact sheet layout required for this workflow to function properly.  
> You must import this sheet into your Google Drive and connect your **Google Sheets API credentials** in n8n.

---

## 🚀 Setup Instructions

1. **Import the workflow** into n8n.
2. **Upload** the provided sample `.xlsx` sheet to Google Sheets.
3. **Connect your credentials:**
   - Google Sheets API
   - Telegram Bot API
4. Adjust:
   - Trigger times (for your timezone)
   - Sheet URL and tab name in each “Read Sheet” node
5. Activate the workflow and watch your productivity reports roll in!

---

## 📈 Why This Helps

This setup gives you:

- Real-time visibility into how your day actually went
- No manual tracking
- A daily accountability nudge straight to your Telegram

It’s like having a personal productivity coach watching your time — but silently.

---

## ❤️ Like the Idea?

If this workflow helps or inspires you,  
please **⭐ star this repo** — it keeps me motivated to share more automations like this!

---

**Tags:** `#Productivity` `#Automation` `#n8n` `#AItools` `#TimeManagement` `#DeepWork` `#BuildInPublic`
