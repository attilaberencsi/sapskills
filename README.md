# SAP Skills

This is a skill repository for SAP Development. It contains general development skills, and ABAP related in first round.

Install all skills from this repository with the skills CLI:

```bash
npx skills add attilaberencsi/sapskills
```

List available skills without installing:

```bash
npx skills add attilaberencsi/sapskills --list
```

Install only the Clean ABAP skill:

```bash
npx skills add attilaberencsi/sapskills --skill clean-abap
```

Install only the Karpathy skill:

```bash
npx skills add attilaberencsi/sapskills --skill karpathy
```

This repository is structured as a multi-skill catalog so additional SAP- and ABAP-related skills can be added over time under `skills/`.

## Available Skills

- `clean-abap`: Apply Clean ABAP guidance when creating, refactoring, reviewing, or explaining ABAP artifacts. Origin:
- `karpathy`: Apply concise behavioral guardrails for coding agents: think before coding, keep solutions simple, make surgical changes, and verify against explicit success criteria.

## Origins

- `clean-abap` is derived from the `CleanABAP.md` guide https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md
- `karpathy` is adapted from the MIT-licensed `karpathy-guidelines` skill in the `multica-ai/andrej-karpathy-skills` repository.
