# Changelog

## 1.1.0 (November 24, 2026)

- Installs as a Claude plugin from this repository, and with `npx skills add` or `gh skill install` in other agents.
- Says at the end of its report when the site a hand-off came from offers a newer version. It only passes this on and never installs anything itself.
- `fetch_handoff.py` adds that notice to `HANDOFF.md`, naming the page only when it's on the hand-off's own site.

## 1.0.0 (November 24, 2026)

- First release: loads Scratch hand-offs, reads frames and flows, builds to the craft rules, then reviews and fixes its own work.
