# Job Gremlin — Plan

Interface: Claude Code skills + one stdlib-only Python fetcher. Output: Markdown only.
Each piece ends with a stop and a test.

## Phase 0 — Scope ✅
- [x] Artifacts: short PRD + working prototype
- [x] Interface: Claude Code skills
- [x] Resume output: Markdown only

## Phase 1 — Plan ✅
- [x] PRD.md
- [x] PLAN.md

## Phase 2 — Data ✅
- [x] `profile.md` format: told / deal-breakers / noticed / change log
- [x] Job listing fields + 3 sample rows; fit = Strong / Possible / Stretch (no % score)
- [x] `voice.md` format: tone / habits / avoid / verbatim example phrases
- [x] Example persona: Sam Rivera (fintech PM → climate tech), all data fictional

### Decisions
- Salary shown exactly as listed, or "Not listed" — never estimated
- Salary floor lives in profile. Jobs below it are hidden by default; if any would otherwise be **Strong** fits, `find-jobs` asks whether to show them

## Phase 3 — Build (one piece per turn)
- [x] 1. Repo skeleton: `.gitignore` (me/, .env), `.env.example`, MIT `LICENSE`, `CLAUDE.md` agent rules, `templates/`, stub README
- [x] 2. Privacy guard: pre-commit hook blocking `me/` and `.env`; `git init`
- [ ] 3. `onboard` skill: interview → `me/profile.md` (create or update)
- [ ] 4. Resume intake inside onboard: PDF/pasted → `me/resume.md`
- [ ] 4b. Voice samples: `me/voice/` folder → editable `me/voice.md` summary (built in onboard; re-runnable)
- [ ] 5. `add-jd` skill: save JD to `me/jds/`, note what fits
- [ ] 6. `tailor-resume` skill: natural tone, change summary, trace-back check
- [ ] 7. `fetch_jobs.py` with Greenhouse/Lever/Ashby (no key)
- [ ] 8. Add Adzuna source (free key)
- [ ] 9. `find-jobs` skill: run fetcher, rank vs. profile, explain each match, list sources searched
- [ ] 10. Profile learning: propose-and-confirm updates + change log
- [ ] 11. `examples/` fictional walkthrough + full README (setup in ~5 steps)

## Phase 4 — Publish
- [ ] Final privacy check of git history, then you push to GitHub

## Open assumptions
- Word resumes: export to PDF or paste text (no .docx parser yet)
- Fetcher uses Python standard library only (no installs)
- Privacy hook lives in tracked `.githooks/`; each clone runs `git config core.hooksPath .githooks` once (in README)
