# job-hunt-os

An evidence-driven, AI-assisted operating system for running a focused job search.

## Skills

### brain-builder

`brain-builder` creates and continuously improves a private career brain from resumes, career documents, or conversation. It preserves source-backed facts, identifies gaps, and asks targeted follow-up questions instead of forcing the user through a fixed questionnaire.

The skill follows the Agent Skills `SKILL.md` format and is intended to be portable across compatible coding agents.

Install with the Agent Skills CLI:

```bash
# Claude Code
npx skills add sichvoge/job-hunt-os --skill brain-builder --agent claude-code

# Codex
npx skills add sichvoge/job-hunt-os --skill brain-builder --agent codex
```

The canonical skill source lives at:

```text
skills/brain-builder/
  SKILL.md
  references/
    brain-layout.md
    evidence-model.md
```

## Private brain data

Job Hunt OS stores your private career brain locally by default under `.brain/`, which is ignored by Git.

Because this brain contains valuable career history that grows over time, we recommend backing it with durable private storage — for example, a private GitHub repository — so it is versioned, recoverable, and available across machines.

The mental model is:

```text
Local .brain/      = working copy
Private Git repo   = recommended durable home / backup
```

Other Job Hunt OS skills should consume the same logical `.brain` interface without depending on the physical storage mechanism.

The initial brain is intentionally small and grows only as real workflows require more structure.