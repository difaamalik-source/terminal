# GoMining Agent Skills (vendored)

The `gomining-*` directories are copied unmodified from
[gomining-ai/gomining-agent-skills](https://github.com/gomining-ai/gomining-agent-skills)
at commit `cac594df3cee4b25e342a846e902f607f956f3e2`, licensed under Apache-2.0
(see `LICENSE-gomining-agent-skills`).

Claude Code loads every `.claude/skills/<name>/SKILL.md` in this repo automatically.

## Updating

```bash
git clone --depth 1 https://github.com/gomining-ai/gomining-agent-skills /tmp/gm-skills
rm -rf .claude/skills/gomining-*
cp -r /tmp/gm-skills/skills/gomining-* .claude/skills/
cp /tmp/gm-skills/LICENSE .claude/skills/LICENSE-gomining-agent-skills
```

Then update the commit hash above.
