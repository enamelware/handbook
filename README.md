# Enamelware handbook

Enamelware makes small, open-source tools for SteamOS-style handhelds and living-room setups, and the product and design systems they share. Every tool feels like part of SteamOS Gaming Mode, works with a controller alone, and does one job. The work is built with AI: decisions are made in conversation, Claude Code writes and tests the code, and a person approves every change and tests it on real devices.

Enamelware is the organisation. Kettle is the app family. Enamel is the design system.

Enamelware is run by the product designer [Mario Carabotta](https://mariocarabotta.com/), who sets its direction and approves every change.

This handbook is how Enamelware works: the principles, standards, workflow and sources that every Enamelware repo follows. It is written for people and for AI tools alike.

## What Enamelware makes

| Name | What it is | Licence | Repo |
| --- | --- | --- | --- |
| Kettle | A family of apps, each named Kettle plus its medium. Kettle Video, a controller-first player for local films and TV shows, is the first | GPL-3.0-or-later | One repo per app |
| Enamel | The design system every Kettle app is styled with: tokens, components, motion, a style guide | MIT | [enamelware/enamel](https://github.com/enamelware/enamel) |
| The handbook | How Enamelware works: principles, standards, workflow, sources | CC BY 4.0 | [enamelware/handbook](https://github.com/enamelware/handbook) |

## Which file to read

Read only what the task needs.

| If you are… | Read |
| --- | --- |
| Deciding anything a spec doesn't cover, stopping, or about to ask a question | [skills/decisions](skills/decisions/SKILL.md) |
| Shaping a feature, naming something, or checking what Enamelware will and won't do (product principles and naming) | [skills/product](skills/product/SKILL.md) |
| Writing or reviewing code, tests, or anything that runs on a device | [skills/development](skills/development/SKILL.md) |
| Building or reviewing anything users see | [skills/design](skills/design/SKILL.md), then Enamel's [DESIGN.md](https://github.com/enamelware/enamel/blob/main/DESIGN.md) |
| Taking work from a problem or opportunity to a release: discovery, shaping, specs, issues, building, testing, releasing | [skills/operations](skills/operations/SKILL.md) |
| Choosing which tool holds what | [docs/tools.md](docs/tools.md) |
| Looking for an outside source | [docs/sources.md](docs/sources.md) |

## Using it

- **Claude Code:** install the handbook as a plugin with project scope. Each skill loads by itself when a task matches it.
- **Other AI tools:** the skills follow the open Agent Skills format. Start from this README and open the one file the task needs.
- **People:** read this README, then the skill for what you're interested in.

## Licence

The text of this handbook is licensed under [CC BY 4.0](LICENSE). Copyright Mario Carabotta.
