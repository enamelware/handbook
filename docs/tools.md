# Tools

Each kind of information has one home. This is the list of tools Enamelware uses, what each is for, and what it is the source of truth for.

| Tool | Used for | Source of truth for | Not for |
| --- | --- | --- | --- |
| GitHub repos | Code, tests, each repo's CLAUDE.md, decision log, DESIGN.md | Everything that ships, and why it was decided | Planning, drafts, private material |
| GitHub issues and the shared board | Every piece of work, from Drafted to Done | What is being built and its status | Discussion that isn't about one issue |
| Claude chats, in one Project | Deciding, specifying, researching, reviewing | Nothing on their own: outcomes move to a repo, an issue or a doc | Building; holding rules only a chat can see |
| Claude Code | Building, testing, writing issues, moving cards | The work itself, inside one repo at a time | Product decisions (see [skills/decisions](../skills/decisions/SKILL.md)) |
| Working docs in claude.ai | The discovery and delivery backlogs, drafts, research, review notes | Work not yet on GitHub | Anything that ships |
| Design canvases in claude.ai | Explorations, mood boards, mockups to react to | Nothing once a direction is chosen: the choice is recorded in a repo | Specs |
| Penpot (planned) | Mockups that become the spec for a screen | Approved screen designs, snapshotted into issues | Tokens and components, which stay in Enamel's repo |
| GitHub Pages (planned) | The published style guide | Nothing new: it shows what Enamel's repo holds | Content of its own |
| Memory (chat and Claude Code) | Personal working context for one actor | Nothing: rules found there move to the handbook or a repo | Organisational rules |

## Rules

- **One home per kind of thing.** If two tools hold the same fact, the one listed as its source of truth wins, and the other is fixed or turned into a link.
- **Chats don't touch repos.** Decisions reach a repo as an issue or a prompt that Claude Code acts on, so every change has a record on GitHub.
- **Nothing important lives only in memory or a chat.** If a future session would need it, it goes in the handbook, a repo or a working doc.
- **A new tool gets a row here before it gets used for real work,** saying what it is the source of truth for.
