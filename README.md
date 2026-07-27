## Code-discipline skills

This repo contains a `code-discipline` skill for codex, modified from Karparthy Guidelines, which tells the code agent to perform minimal correct edits and avoid defensive checks.

The repo consists of a very general `codex/AGENTS.md` that tells the agent to use this skill and follow.
Specific projects can also have their own prompts (maybe tracked by git), so the overall layout is like the following:

```
~/.codex/
└── AGENTS.md                         # Small personal defaults and skill trigger

~/.codex/skills/
└── coding-discipline/
    ├── SKILL.md                      # Canonical behavioral guidelines
    └── EXAMPLES.md                   # Optional examples

<project_repo>/
├── AGENTS.md                         # Repo-specific instructions
└── submodule/
    └── AGENTS.md                     # Submodule-specific overrides
```

### Usage 

``` bash
# Clone this repo, for example to ~/git/code-discipline

ln -s ~/git/code-discipline/codex/AGENTS.md ~/.codex/AGENTS.md
ln -s ~/git/code-discipline/skills/code-discipline ~/.codex/skills/code-discipline

```