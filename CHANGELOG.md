# Changelog

## 1.2.0 (November 24, 2026)

- One copy of the skill, with no scripts, so the same repository installs everywhere and can go to Claude's plugin directory, which only accepts scripts from verified organizations.
- Downloads and checks a hand-off itself: only the files its manifest lists, only from the hand-off's own address, with size limits and SHA-256 checks.
- Adds the Scratch icon.

## 1.1.0 (November 24, 2026)

- Installs as a Claude plugin from this repository, and with `npx skills add` or `gh skill install` in other agents.
- Says at the end of its report when the site a hand-off came from offers a newer version. It only passes this on and never installs anything itself.

## 1.0.0 (November 24, 2026)

- First release: loads Scratch hand-offs, reads frames and flows, builds to the craft rules, then reviews and fixes its own work.
