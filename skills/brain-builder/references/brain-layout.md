# Brain Storage Contract

Brain Builder needs a private place to store career source material and generated brain state.

The brain is local by default. Because it contains valuable career history that grows over time, Brain Builder should recommend backing it with durable private storage — for example, a private GitHub repository — so it is versioned, recoverable, and available across machines.

The user experience should stay the same regardless of how the brain is backed up or synchronized.

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

## Local brain

By default, `.brain/` exists inside the Job Hunt OS working directory and must be excluded from Git.

The repository should include:

```gitignore
.brain/
```

Brain Builder should warn if any `.brain` file is already tracked by Git.

The local brain is the working copy used by Job Hunt OS. Local-only storage is convenient but can be lost and does not automatically provide history, backup, or synchronization across machines.

## Recommended durable storage

Brain Builder should recommend backing the local brain with durable private storage. A private Git repository, such as a private GitHub repository, is the recommended initial approach because it provides:

- history and rollback,
- remote backup,
- multi-machine sync,
- visibility into how the brain evolved.

The mental model is:

```text
Local .brain/      = working copy
Private Git repo   = recommended durable home / backup
```

The public Job Hunt OS repository should still present the brain through the same logical `.brain` path. The exact implementation may use a symlink, configurable path, worktree, or another portable mechanism.

Durable private storage is recommended, but it must not be mandatory for bootstrap. A user should be able to start locally and configure durable storage later.

Brain Builder must never make a private brain repository public.

## Storage setup behavior

When creating a new brain, do not block bootstrap on storage configuration unless persistence is technically required by the current environment.

If no storage preference exists:

1. explain briefly that the brain contains private career data,
2. create or use a safe local private brain when appropriate,
3. recommend durable private storage such as a private GitHub repository for backup, version history, and multi-machine access,
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