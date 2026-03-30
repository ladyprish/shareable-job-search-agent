# Build Your Own Job Search Agent — Claude Code Instructions

## How to Use This

1. Install Claude Code (https://claude.com/product/claude-code)
2. Open Terminal and create a project folder:
   ```
   mkdir -p ~/Projects/job-agent
   cd ~/Projects/job-agent
   ```
3. Save this file in that folder as `job-agent-project-instructions.md`
4. Start Claude Code by typing `claude`
5. Paste the kickoff message at the bottom of this document to get started

Before you begin, fill in the sections marked with [FILL IN] below. The more specific you are, the better your matches will be.

---

## About Me

### My Background
[FILL IN: Your work history, key roles, industries, years of experience, and major accomplishments. Be specific — instead of "marketing experience," write "7 years in B2B SaaS product marketing, launched 3 products from 0 to 1, led rebrands at two startups."]

### My Skills
[FILL IN: Technical skills, tools, certifications, soft skills, languages. Example: "HubSpot, Salesforce, SQL, product positioning, competitive analysis, cross-functional leadership."]

### My Education
[FILL IN: Degrees, relevant coursework, ongoing learning. Example: "MBA from UT Austin, Google Analytics certified, currently completing Reforge growth series."]

---

## What I'm Looking For

### Target Roles
[FILL IN: Job titles, functions, seniority level. Example: "Founding Marketer, Head of Product Marketing, first marketing hire — IC or player-coach, not managing a large team."]

### Target Industries / Company Types
[FILL IN: Example: "B2B SaaS startups, Series A or earlier, building from 0 to 1. Interested in fintech, developer tools, or healthcare tech."]

### Location / Remote Preferences
[FILL IN: Example: "Remote only. Open to occasional travel for offsites. Must be US-based company or open to US time zones."]

### Compensation Range
[FILL IN: Example: "$140K–$180K base plus meaningful equity. Flexible on base if equity is substantial."]

### Company Culture / Values
[FILL IN: Example: "Small, scrappy team. Founder-led. Writing culture over meeting culture. High autonomy."]

### Other Preferences
[FILL IN: Anything else that matters to you. Example: "I want to be the one writing the marketing playbook, not inheriting one. Want direct access to founders and customers."]

---

## What I'm NOT Looking For (Deal-Breakers)

[FILL IN: Be specific. These are instant disqualifiers. Example:
- No agencies or consultancies
- No companies with 500+ employees
- No roles that report to a VP of Sales
- No crypto/web3
- No roles requiring 5 days in-office]

---

## Job Sources to Search

Check the ones that are relevant and add any specific companies:

- [ ] LinkedIn Jobs (public listings)
- [ ] Indeed
- [ ] Glassdoor
- [ ] We Work Remotely
- [ ] Hacker News "Who's Hiring"
- [ ] AngelList / Wellfound
- [ ] Other: [FILL IN]

### Specific Companies to Watch
[FILL IN: Companies whose career pages you want checked daily. Example:
- Notion (notion.so/careers)
- Linear (linear.app/careers)
- Vercel (vercel.com/careers)]

---

## Delivery Preferences

- **Format**: One daily email with all matches
- **Delivery time**: [FILL IN: Example: "By 8:00 AM Central"]
- **Email address**: [FILL IN: The email where you want to receive matches]
- **Minimum fit score**: [FILL IN: 1–10 scale, default is 7. Higher = pickier, fewer results. Lower = more results, some noise.]

### What Each Job in the Email Should Include
- Company name
- Role title
- Why it's a match (1–2 sentences)
- Fit score
- Link to the full posting

---

## What the Agent Does

Here's what you're building:

1. **Knows you deeply** — It works from the profile you filled in above to understand your experience, skills, and exactly what you want (and don't want).

2. **Searches for jobs daily** — It checks public job boards and company career pages overnight for new listings.

3. **Scores every listing** — It uses the Claude API to read each posting and compare it against your profile. Not just keyword matching — it understands that "Director of Product, Enterprise Software" might be a match even if you wrote "Senior Product Manager at a B2B SaaS company."

4. **Sends you only the best fits** — One email each morning, sorted by fit score. No duplicates across days.

---

## Architecture

```
my-profile.md          ← Your qualifications and preferences
        ↓
search module          ← Searches public job boards, collects listings
        ↓
scoring module         ← Sends each listing + your profile to Claude API for scoring
        ↓
email module           ← Formats top matches and sends via email
        ↓
scheduler (cron)       ← Runs the whole pipeline daily
```

---

## What You Need to Set Up

You'll need three things. Claude Code will help you use them, but you need to create them:

### 1. Anthropic API Key (for job scoring)
- Go to console.anthropic.com
- Create an account and add an API key
- Add billing — job scoring costs roughly $0.50–$2.00/day depending on how many listings it processes

### 2. Email Service API Key (for sending the daily email)
- Easiest option: Resend (resend.com) — generous free tier
- Other options: SendGrid (free tier) or Gmail SMTP with an App Password

### 3. This Document (filled in with your details above)

---

## Build Phases

Claude Code will walk you through each phase:

**Phase 1: Project Setup** — Create the project structure, CLAUDE.md, and your profile document.

**Phase 2: Job Searcher** — Build a script that searches public job boards and collects listings. Start with one source, then add more.

**Phase 3: Job Scorer** — Connect to the Claude API. Score each listing against your profile. Filter by threshold. Track seen jobs to prevent duplicates.

**Phase 4: Email Sender** — Connect to your email service. Format a clean, scannable daily digest.

**Phase 5: Connect Everything** — Build the pipeline that runs search → score → email in order. Test end to end.

**Phase 6: Schedule It** — Set up a daily cron job on your Mac so it runs automatically every morning.

---

## Important Notes

- **No account logins**: The agent only accesses publicly available job pages. It never logs into LinkedIn or any platform as you. This protects your accounts.
- **You don't need to be a developer**: If you've never used Terminal before, that's fine. Claude Code will explain every step.
- **You can refine over time**: If matches are too broad, raise your fit score threshold or add deal-breakers. Too narrow, lower the threshold or broaden your preferences.

---

## Kickoff Message

Once you've filled in your details above and started Claude Code in your project folder, paste this:

> Read the file `job-agent-project-instructions.md` in this folder. This is the master plan for what we're building. Let's start with Phase 1 — help me set up the project, create the CLAUDE.md, and then build my-profile.md from the details I've provided in the instructions file. Walk me through every step in plain language — I'm new to Terminal and Claude Code.

---

*Originally built by Jennifer Prishtina. Adapted for sharing.*
