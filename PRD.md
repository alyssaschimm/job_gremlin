# Job Gremlin — PRD

*Living document. Last updated 2026-11-18.*

## Overview
Job Gremlin is an open-source job-search assistant that runs inside Claude Code. It interviews users to learn what they want from their next role, finds job listings that fit, and rewrites their resume for a specific job without using exact language from the job description. Anyone can fork it and use it with their own data. That data stays on their own computer.

## Problem and value
Job searching takes a lot of repetitive work: re-explaining what you want, digging through listings that don't fit, and rewriting your resume for each application. Most tools either stuff your resume with the posting's keywords (which reads as robotic) or don't tailor it at all.
**What it offers:** a single profile of who you are and what you want, which gets better over time, and which drives both the job search and the resume tailoring. Everything it writes is honest and sounds human.

## Persona
**The deliberate job seeker.** A mid-career professional (for example, a PM or designer) who knows roughly what they want but not every company that offers it. They're comfortable opening a terminal app if the steps are spelled out. They care more about fit than volume, and they're uneasy about AI-written resumes that overstate their experience.

## User stories
1. As a job seeker, I can describe the kind of role I want, my interests and my deal-breakers in a conversation, and get back a saved profile I can read and edit.
2. As a job seeker, I can add my current resume once and have it reused for everything.
3. As a job seeker, I can add job descriptions I like so the system learns what draws me to a role.
4. As a job seeker, I can ask for a resume tailored to a specific job, see what changed and why, and trust that nothing was made up.
5. As a job seeker, I can ask for a fresh list of matching jobs, ranked, with a plain-language reason for each match.
6. As a job seeker, I'm asked before my profile changes based on something the system noticed, and I can see how my profile has changed over time.
7. As a job seeker, I can add samples of my own writing (posts, cover letters, notes) so tailored resumes sound like me, not like AI.
8. As someone forking the repo, I can set it up in about 5 steps without touching anyone else's personal data.

## Features
| Feature | What it does |
|---|---|
| **Onboard** | A conversational interview that writes or updates your profile. Can be re-run at any time. |
| **Resume intake** | Converts your PDF or pasted resume into one editable master copy. |
| **Add JD** | Saves a job description you like and notes what about it fits your profile. |
| **Voice samples** | You drop examples of your own writing into a private folder. The system learns your word choice, sentence rhythm and phrasing, and saves a short voice summary you can read and edit. |
| **Tailor resume** | Rewrites your resume for one job in your voice, with a summary of what changed and why. Flags any line that can't be traced back to your original resume. |
| **Find jobs** | Pulls current listings from public job-board feeds, ranks them against your profile, and explains each match. |
| **Profile learning** | Suggests profile updates based on your patterns. Nothing is saved without your approval, and every change is logged. |

## User flow
Clone the repo and add your keys → **Onboard** (interview plus resume) → optionally add **voice samples** and **Add JD** a few times → **Find jobs** → pick one → **Tailor resume** → review the changes → apply on your own.

## Requirements (non-functional)
- **Privacy:** personal data is never committed to git. The repo has safeguards against doing it by accident.
- **Honesty:** tailored resumes contain no invented experience, titles, numbers or skills.
- **Plain language:** every output can be read without knowing any job-search jargon.
- **Lightweight:** no web app, no database, minimal dependencies. Free job sources come first.
- **Forkable:** ships with a fictional example person, so the repo can be shown off without exposing real data.

## Out of scope (for now)
Automatically submitting applications, cover letters, Word/PDF resume output, tracking application status, and LinkedIn or Indeed listings (their terms forbid automated collection).

## Assumptions, dependencies, constraints
- The user has Claude Code installed and a Claude subscription or API access.
- Job sources: the Greenhouse, Lever and Ashby public job feeds (no key, searched one company at a time) and Adzuna (free key, searches across companies). Coverage is limited to companies that post through these.
- PDF resumes can be read directly. Word files must be exported to PDF or pasted in as text.
- Voice samples are optional and should be the user's own, mostly unedited writing. Voice shapes tone and phrasing, but the resume stays concise and professional. Without samples, the tone defaults to "natural."
- Resume tone is set to "natural" by default. Standard skill names are still used where they're true, so automated resume filters don't reject the resume.

## Risks
- **Job feed coverage gaps:** many companies won't appear. The tool says which sources were searched, so users know what's missing.
- **Keyword filters:** a casual tone may score lower in automated resume filters. This is lessened by keeping standard skill names.
- **Exaggeration:** the AI may overstate experience. This is lessened by the trace-back check and the "what changed" summary.
- **Voice overreach:** copying the user's style too closely could make a resume too casual. This is lessened by the editable voice summary and keeping standard resume structure.
- **Profile drift:** inferred preferences may be wrong. This is lessened by asking before every update, keeping inferred items in their own section, and logging changes.

## Success metrics
- A new user goes from cloning to a first ranked job list in under 20 minutes.
- At least half of the top 10 ranked jobs are ones the user would consider applying to.
- A tailored resume needs only light edits before sending, with zero claims that can't be traced back to the original.
- Zero personal files ever committed, checked against the fictional example data.
