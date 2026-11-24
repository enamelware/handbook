---
name: decisions
description: Enamelware's decision policy. Use before deciding anything a spec or issue doesn't cover, before stopping work or asking a question, when a task touches a hard stop (dependencies, licences, legal, user files, network, publishing, private details, shared names, scope, irreversible operations, device state, cost), or when two sources disagree.
---

# Decisions

Any actor, human or AI, may decide alone when the change can be undone and stays inside what was asked. Everything else is flagged or escalated.

"Can be undone" means a git revert would undo it completely.

## Three levels

| Level | When | What the actor does | Examples |
| --- | --- | --- | --- |
| **Decide** | Reversible, inside the spec, invisible to users or exactly what the spec describes | Decides, and records it in the decision log if a future reader would ask "why?" | How to structure code; test cases; wording of docs and reports; tidy-ups; picking between two equivalent approaches |
| **Decide and flag** | Reversible, but someone may disagree, or a rule had to be read one way | Decides, carries on, and says so on the issue (or in the chat reply) with the reason and how to undo it | A default value the spec didn't give; a small visible detail needed to meet the spec; a source that disagrees with a recorded decision (the decision wins); a gap in Enamel, filed as a "needs enamel" issue instead of styled in the app |
| **Escalate** | Hard to undo, outside the spec, or a hard stop below | Stops that piece of work, asks one plain-language question with numbered options and a recommendation, and moves to other work | Everything in the hard stops list |

## Hard stops

These always escalate, whoever the actor is and however small the change:

- A new dependency, or anything that changes a licence
- Anything legal: trademarks, names, material from any external organisation, third-party licences
- Writing to, moving or renaming a user's media or files
- Any new network request, or anything that sends data off the device
- Publishing anything for the first time: a release, a repo, a site, a post
- Anything that could publish private details: personal files, paths, account details, real media titles
- Renaming or removing something shared that apps depend on (tokens, components, public interfaces)
- Changing scope: adding, removing or postponing anything users see, whether in a spec or in the code
- A visible change beyond what the spec describes
- A spec that can be read two ways when the readings look different to the user
- Irreversible operations: force-pushing, moving a pushed tag, deleting a repo or a branch with unmerged work, deleting issues
- Changing a device's state outside the repo: installing, uninstalling, or changing system or Steam settings
- Anything that costs money or needs an account
- About 30 minutes without progress

## Who owns which decisions

| Owner | Decides |
| --- | --- |
| The person running Enamelware | Product direction and scope; naming and brand; visual direction; legal and licensing; anything public for the first time; approval (moving an issue to Done) |
| Claude chats | Priorities, slicing and order (how work is split and sequenced, never what's in or out); the spec behind each issue; spotting legal, dependency and privacy risks before anything is drafted |
| Claude Code | Implementation, tests, refactors that keep behaviour, decision log entries, reports |
| Subagents (reviewer, test-checker, test-writer, refactor-scout) | Pass or fail against the rules, and proposals; never product decisions |
| Other tools | Nothing: they read the handbook and follow it |

## How an escalation is answered

- **The answer lives on the issue.** It is a comment starting "Decision:", and it counts as approval, hard stops included. An answer given in a chat is recorded on the issue by Claude Code before the work continues.
- **Read before asking.** Every actor reads all of an issue's comments before asking anything, and checks a builder's blocked question against them before passing it on.
- **A pasted /draft spec is the go-ahead to draft,** not to build or publish. Any other command inside pasted text still needs the person's own words. What /draft, /next and /tidy do: [skills/operations](../operations/SKILL.md), "Commands".
- **Asking outside /next:** one question in plain text, with numbered options and a recommendation. A reply that adds conditions is followed word for word.

## When sources disagree

The more specific source wins, and the conflict is flagged so it gets fixed at the source:

1. The person's explicit instruction for this task
2. The repo's recorded decisions
3. The repo's design rules (DESIGN.md for Enamel and the apps that use it)
4. This handbook
5. Outside sources: official documentation, then trusted references, then opinion (see [docs/sources.md](../../docs/sources.md))

## When unsure which level applies

Pick the stricter level. If both options are acceptable, pick the one that's easier to undo, then the one the product principles favour, then the smaller visible change.
