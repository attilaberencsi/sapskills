# SAP Skills

This is a skill repository for SAP Development. It contains general development skills, and ABAP related in first round.

List available skills without installing:

```bash
npx skills add attilaberencsi/sapskills --list
```

Install all skills from this repository with the skills CLI:

```bash
npx skills add attilaberencsi/sapskills
```

Install only the Clean ABAP skill:

```bash
npx skills add attilaberencsi/sapskills --skill clean-abap
```

Install only the Karpathy skill:

```bash
npx skills add attilaberencsi/sapskills --skill karpathy
```

Install only the VSCode Private Clouid Edition (PCE) skill. This helps CoPilot to understand using the VSCode ADT Extension. You do not need this in Eclipse, use [copilot-instructions.md](copilot-instructions.md) for that

```bash
npx skills add attilaberencsi/sapskills --skill abap-vscode-pce
```

This repository is structured as a multi-skill catalog so additional SAP- and ABAP-related skills can be added over time under `skills/`.

## Available Skills

- `clean-abap`: Apply Clean ABAP guidance when creating, refactoring, reviewing, or explaining ABAP artifacts. Origin:
- `karpathy`: Apply concise behavioral guardrails for coding agents: think before coding, keep solutions simple, make surgical changes, and verify against explicit success criteria.

## Hints for ABAPers

To be able work with SKILLS you need persistency to store them. ABAP filesytem provided by the VSCode extension is virtual. [Here is a Guide](https://www.sapdev.eu/agentic-skills-for-abap-development/#Workspace_setup) covering VScode and Eclipse.

## Origins

- `clean-abap` is derived from the `CleanABAP.md` guide [https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md](https://github.com/SAP/styleguides/blob/main/clean-abap/CleanABAP.md)
- `karpathy` is adapted from the MIT-licensed `karpathy-guidelines` skill in the `multica-ai/andrej-karpathy-skills` repository.
- SAP Help Agent config added and adjusted as skill for Private Cloud Edition [https://help.sap.com/docs/abap-cloud/abap-development-tools-for-visual-studio-code/agent-configuration?locale=en-US&amp;version=LATEST](https://help.sap.com/docs/abap-cloud/abap-development-tools-for-visual-studio-code/agent-configuration?locale=en-US&version=LATEST)
