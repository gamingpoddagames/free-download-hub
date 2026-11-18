# School Daily Content Automation — No AI

Workflow: `.github/workflows/school-daily.yml` at 08:47 Sri Lanka time every day (GitHub scheduler may be delayed).
The script uses **only Python standard library**, a reviewed original question bank, and deterministic rotation.
No ChatGPT or paid AI API required. 14 reviewed sample questions repeat after 14 days until more are added.

## Content generated
- `facebook_post.txt` — Sinhala question, choices, correct answer and explanation
- `printable.html` — browser-printable single-question worksheet plus answer page
- `question.json` — structured quiz content

Each run uploads these as a GitHub Actions artifact (30-day retention).

## Enable Facebook publication
Create GitHub Actions repository secrets **FB_PAGE_ID** = 61596326146776 and **FB_PAGE_ACCESS_TOKEN** = a valid Page token.
The Page must be administered by the token holder and the Meta app must have sufficient permissions (including pages_manage_posts and any required approval). No credentials are saved to repository files.
When both secrets exist, scheduled runs try to publish through the Meta Graph API. If they don't, scheduled runs generate files only.
Manual runs default to **publish=false**, making tests safe. A manual run with publish=true posts publicly, if credentials are configured.
Failures are visible in GitHub Actions logs. Facebook post success is confirmed only when a post ID is returned.

## Limitations
- No automated new question invention: question bank cycles by date.
- This workflow does not yet publish MP4 videos, post PDF uploads, update the website, or guarantee Facebook publishing without valid permissions.
- No fake traffic or ad-click automation.
- Please review new bank entries before adding. Extend the bank for unique daily content.
