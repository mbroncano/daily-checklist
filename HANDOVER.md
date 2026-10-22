# Homework checklist — handover prompt

Give this to your own AI assistant (Muse, ChatGPT with its browser, OpenClaw, or a similar agent). It describes the loop and the rules behind the daily homework checklist page, platform-neutral. Fill in the [bracketed] parts when your assistant asks.

Published copy: https://mbroncano.github.io/daily-checklist/handover.html

---

I want you to build and run a daily homework checklist system for my child, modeled on a system a friend of mine uses. Read this whole brief before starting, and ask me about anything marked [in brackets] that you need from me.

THE SYSTEM, IN ONE PARAGRAPH
Every school-day morning, you check my child's school systems yourself, rebuild a short list of what is open, overdue, or due soon, publish that list to a simple web page my child opens on their phone, and send me a short report of what is new. The page is just a checklist. The intelligence is in your checking.

PART 1 — THE DAILY CHECK (the important part)
- Systems to check: [the grade portal, e.g. PowerSchool parent portal, with its web address] and [the course platform, e.g. Canvas, and how we reach it, e.g. through our district's single sign-on]. Also [any linked practice tools teachers assign work in, e.g. a math practice app].
- Access is READ-ONLY. Never submit, answer, post, message, or change anything in the school systems. Never press Send, Submit, Begin, or Start on anything. You are an inspector, not a student.
- Check EVERY open item in every system, not just what the dashboards highlight. For each new item, open its detail page and read the instructions before deciding how it gets done: a computer submission, an external practice tool, paper done at home, or work that can only happen at school. Never classify an item from its title alone.
- Items that are still locked or not yet available do NOT go on my child's list. They join the list only once they are actually available.
- When my child says something is done, treat it as a claim. It counts as done only when a school system confirms a submission or a score. If a system cannot confirm it either way, say so plainly instead of guessing.
- QUIZ WARNING, learned the hard way: when you inspect a quiz, look only at the grades page and the assignment detail page. Never open the quiz itself (the "take" view). On some platforms, opening it starts an empty attempt, and if the quiz then locks, that empty attempt can be submitted automatically and scored zero.
- If a login fails, retry once before reporting it broken. School portals fail transiently and have district-wide outages; neither is a broken password.

PART 2 — THE LIST
Keep the current list as one small data file (JSON works well), one entry per item: a stable id, subject, title, kind (laptop / paper / school), due date, a one-sentence note written for my child in plain language saying where the work lives and what to do next, and a status (open / verified). "Verified" only when a school system confirms it. Include overdue items, items due within 3 days, blocked items (e.g. a locked quiz my child must ask the teacher about), and items verified done in the last 2 days.
- NEVER put grades or scores in this file. The hosting is public (see Part 3), so treat everything in the file as readable by anyone who has the link.
- Stamp the file with the time it was last updated.

PART 3 — THE PAGE
One static web page: no server, no accounts, no login. Host it somewhere free and simple (GitHub Pages works; note its free tier requires a public repository, which is why Part 2 forbids sensitive data). The page reads the data file and shows:
- A gentle, calm design: soft colors, readable cards, a small subject label per item. Urgency shown with mild color tints and colored due-date text, never alarms.
- A "Tonight's mission" counter and a simple progress bar.
- Check-off taps stored only on my child's phone (browser local storage). His taps are claims and must look different from "verified" items.
- A visible warning if the list is more than about a day old.
- When everything is verified done: one small celebration, a single brief confetti wave, once. No streaks, no points, no leaderboards, no notifications.

PART 4 — REPORTING TO ME
Each morning after the check, send me a short report of what is NEW only: new missing or overdue work, grade changes worth knowing, anything blocked that needs a person. Group the home-doable items into laptop and paper. Things already reported stay quiet unless they change. If a check cannot run, tell me which part failed and why.

SETUP ORDER
1. Ask me for: my child's first name and grade, the school's name, the portals' web addresses, and how sign-in works. I will give credentials only through your platform's secure credential storage, never pasted into chat.
2. Do one supervised manual check while I watch, and show me the list before you publish anything.
3. Only after that, set up the recurring morning check ([suggested: 7:00am local time]) and the page publishing.
4. Keep a private record of what you have already reported to me, so you never report the same item twice.

Start with step 1: tell me what you need from me.
