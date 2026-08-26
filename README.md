# rigorous-proofs

An Agent Skill (packaged as a Claude Code plugin + self-hosting marketplace) that gets
an AI agent to produce **rigorous, verifiable mathematical proofs** via a
`plan → prove → verify → revise` loop. Pure Markdown — no runtime, no dependencies.

## Layout

```
skill-solve-math/
├── .claude-plugin/
│   ├── plugin.json          # plugin manifest
│   └── marketplace.json     # marketplace catalog (source "./")
├── skills/rigorous-proofs/
│   └── SKILL.md             # the whole skill, one file
├── rigorous-proofs.skill    # prebuilt bundle for claude.ai upload
├── README.md
└── LICENSE
```

## Install

**As a plugin:**

```
/plugin marketplace add ictumuk/skill-solve-math
/plugin install rigorous-proofs@proof-skills
```

Test locally first from the repo root: `/plugin marketplace add .` then the install line.
Manage with `/plugins`. Docs: <https://code.claude.com/docs/en/plugins>

**As a bare skill:**

| Agent            | Where to copy `skills/rigorous-proofs`        | Invoke                     |
| ---------------- | --------------------------------------------- | -------------------------- |
| Claude Code      | `~/.claude/skills/` or `.claude/skills/`      | auto; `/reload-skills`     |
| Codex CLI        | `.agents/skills/` or `~/.agents/skills/`      | auto, `$`, or `/skills`    |
| Gemini CLI       | `.agents/skills/`                             | auto                       |
| Cursor           | `.cursor/skills/`                             | auto                       |
| VS Code Copilot  | `.github/skills/`                             | `/`                        |

**Claude.ai:** open the `.skill` file, click **Save skill**.
**No skill system:** paste `SKILL.md` into the system prompt.

## Publish

```bash
git init && git add . && git commit -m "rigorous-proofs"
git remote add origin git@github.com:ictumuk/skill-solve-math.git
git branch -M main && git push -u origin main
```

Repo must be **public** (marketplaces are fetched from GitHub). Validate manifests with
`claude plugin validate .`.

## License

MIT — see [LICENSE](LICENSE).
