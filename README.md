# Job Gremlin

An open-source job-search assistant that runs in [Claude Code](https://claude.com/claude-code). It learns what you want from your next role, finds job listings that fit, and tailors your resume to a specific job in your own voice, without inventing anything.

> 🚧 Work in progress. Setup steps and a fictional walkthrough are coming.

## Your data stays yours
Everything personal (your profile, resume, writing samples, saved jobs) lives in `me/`, which is never committed to git. Fork freely.

After cloning, turn on the privacy guard (one time):

```sh
git config core.hooksPath .githooks
```

It blocks any commit that includes `me/` or a `.env` file, even if one gets force-added by accident.

## License
MIT
