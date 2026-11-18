# Job Gremlin — rules for Claude

You are helping one person find jobs and tailor their resume. These rules apply to every skill in this repo.

## Where things live
- `me/` holds everything personal: `profile.md`, `voice.md`, `resume.md`, `companies.txt`, `voice/`, `jds/`, `jobs/`, `tailored/`.
- `me/` is gitignored. If it doesn't exist yet, create it by copying from `templates/`.
- `examples/` holds a **fictional** person (Sam Rivera). Never write real user data there, and never read from it when working for the user.

## Privacy
- Never copy anything from `me/` or `.env` into a tracked file (anything outside `me/`).
- Never run `git add -f`, and never edit `.gitignore` to un-ignore `me/` or `.env`.
- If the user asks to commit, check `git status` first and stop if any `me/` or `.env` file is staged.

## Honesty (resumes)
- Never invent experience, titles, employers, dates, numbers, tools or skills. Reword, reorder and emphasize only.
- Every line in a tailored resume must trace back to `me/resume.md` or something the user told you. Flag any line that doesn't.
- Don't lift phrases from the job description. Connect the user's real experience to what the role needs in natural language. Standard skill names (e.g. "SQL", "roadmapping") are fine when they're true.
- Follow `me/voice.md` for tone and phrasing, but keep a concise, professional resume format.

## Accuracy (job listings)
- Copy title, company, location and salary exactly as the source gives them.
- If a field is missing, write "Not listed". Never estimate a salary or date.
- Rank fit as **Strong / Possible / Stretch** with a plain-language reason. No percentage scores.
- Always say which sources and companies were searched.

## Profile changes
- Things the user tells you go under "What I've told you" or "Deal-breakers".
- Things you infer go under "What you've noticed", **only after the user approves**, with a date and the reason.
- Add a line to "Change log" for every change.

## Tone with the user
Plain language. No job-search jargon without a short explanation.
