# Scratch design: the copy for Claude's plugin directory

This folder is the plugin as submitted to Claude's plugin directory. It's the same skill as `skills/scratch-design` at the top of this repository, without the `scripts` folder, because the directory only accepts scripts from verified organizations. Without the script, the skill downloads and checks a hand-off itself, following the same rules.

Install instructions for every tool are in the [main README](../README.md).

When the skill changes, copy `skills/scratch-design` into `claude-directory/skills/` again, leave out `scripts`, and keep the version in `.claude-plugin/plugin.json` the same as the one at the top.
