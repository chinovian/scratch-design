# Changelog

## 1.1.1 (November 24, 2026)

- Works without its download script: when `scripts/fetch_handoff.py` isn't there, it downloads and checks a hand-off itself, following the same rules.
- Adds `claude-directory/`, the copy submitted to Claude's plugin directory, which leaves the script out because the directory only accepts scripts from verified organizations.
- Adds the Scratch icon.

## 1.1.0 (November 24, 2026)

- Installs as a Claude plugin from this repository, and with `npx skills add` or `gh skill install` in other agents.
- Says at the end of its report when the site a hand-off came from offers a newer version. It only passes this on and never installs anything itself.
- `fetch_handoff.py` adds that notice to `HANDOFF.md`, naming the page only when it's on the hand-off's own site.

## 1.0.0 (November 24, 2026)

- First release: loads Scratch hand-offs, reads frames and flows, builds to the craft rules, then reviews and fixes its own work.
