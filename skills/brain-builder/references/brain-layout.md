# Brain Storage Contract

Brain Builder needs a private, durable place to store career source material and generated brain state.

The skill must support two storage modes:

1. local private storage,
2. private Git-backed storage.

The user experience should stay the same regardless of storage mode.

## Logical brain root

The skill should operate against a single logical brain root called `.brain`.

Other Job Hunt OS skills should also read from this logical root rather than knowing how the data is physically stored.

Recommended initial layout:

```text
.brain/
  sources/
    current-resume.md
    interviews/
  evidence.yaml
  metadata.yaml
```

Do not create additional files or directories until they are needed by a real workflow.

## Local mode

In local mode, `.brain/` exists inside the Job Hunt OS working directory and must be excluded from Git.

The repository should include:

```gitignore
.brain/
```

Brain Builder should warn if any `.brain` file is already tracked by Git.

Local mode is simple but not durable by itself. The user should be told that local-only storage can be lost and does not automatically sync across machines.

## Private Git-backed mode

In Git-backed mode, the private brain is stored in a separate private repository or another private Git worktree.

The public Job Hunt OS repository still presents the brain through the same logical `.brain` path. The exact implementation may use a symlink, configurable path, or another portable mechanism.

Do not assume a second repository is mandatory. It is a durability option.

Benefits include:

- history and rollback,
- remote backup,
- multi-machine sync,
- visibility into how the brain evolved.

The private repository must never be made public by Brain Builder.

## Storage setup behavior

When creating a new brain, do not block bootstrap on storage configuration unless persistence is technically required by the current environment.

If no storage preference exists:

1. explain briefly that the brain contains private career data,
2. default to a safe local private brain when appropriate,
3. mention that a private Git-backed brain is available for durable history and backup,
4. let the user decide whether to configure durable storage now or later.

Do not turn storage setup into a long onboarding flow.

## Source material

Source material is durable input to the brain and must be preserved.

Examples:

- imported resume text,
- user-provided career documents,
- Brain Builder interview transcripts,
- explicit career notes supplied by the user.

Suggested layout as sources grow:

```text
.brain/sources/
  current-resume.md
  interviews/
    2026-09-09-kong-analytics.md
  imports/
    performance-review-2025.md
```

Create these subdirectories only when needed.

## Generated files

Generated files should clearly state that they are derived and should not be edited directly.

At minimum:

```text
.brain/evidence.yaml
```

The evidence file should be reproducible from preserved source material as far as practical.

## Privacy safeguards

Brain Builder must not:

- commit private career data to the public Job Hunt OS repository,
- copy `.brain` content into examples or fixtures,
- publish a private brain repository,
- expose secrets found in imported material unnecessarily.

If `.brain` is located inside a Git repository, check whether it is ignored before writing sensitive data when the environment makes that possible.

## Portability

Do not depend on Claude-specific, Codex-specific, or vendor-specific paths for brain storage.

Agent-specific installation directories contain the skill. The user's career brain belongs to the Job Hunt OS workspace or configured private storage, not inside the installed skill directory.