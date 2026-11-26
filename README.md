# Ytlive — 24/7 YouTube Live Loop

Streams a 6-minute loop video to YouTube Live around the clock, using GitHub
Actions (free on a public repo). No server, no monthly fee.

## How it works

- **Loop video:** `loop.mp4` — 13 free stock clips (Pexels, no watermarks) +
  dark suspense BGM (Kevin MacLeod, CC-BY — credit in the live description).
  It lives as a Release asset (`loop-v1`), not in the repo.
- **Workflow:** `.github/workflows/stream.yml` — each run streams ~5.5 hours
  with ffmpeg, then re-dispatches itself. A cron every 6 hours is the backstop.
- **Stream key:** stored as a repo secret `YT_STREAM_KEY` (YouTube Studio →
  Go Live → Stream key). Never commit it.

## Notes

- One Actions job caps at 6 hours, so the live drops for 1–2 minutes at each
  restart, then resumes on the same stream.
- Actions is built for CI/CD — running a 24/7 stream bends the rules, so
  there is a small risk GitHub flags the account.
