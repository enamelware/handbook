---
name: operations
description: How work moves at Enamelware, from a problem or opportunity to a release. Use when logging or assessing a problem or opportunity, working on either backlog, shaping or speccing work, writing a /draft prompt or an issue, running /draft, /next or /tidy, moving cards on the board, testing, handing work between sessions or devices, writing a report, or preparing a release.
---

# Operations

Every piece of work takes the same route, from a problem or opportunity to a release. Work starts from a problem someone has, never from a solution looking for one. Decisions happen in conversation, Claude Code builds and tests, and a person approves. Who may decide what at each stage is in [skills/decisions](../decisions/SKILL.md).

## From opportunity to delivery

| Stage | What happens | Where | Who |
| --- | --- | --- | --- |
| 1. Problem or opportunity | A problem or opportunity is logged: who has it, what they do about it today, the evidence for it, and the tools that already address it, including ones that only partly overlap | The discovery backlog | Anyone; logged in a chat |
| 2. Discovery | Possible solutions explored, competitors checked, assumptions written down, spikes and experiments where facts are unknown. Ends with a decision: solve it, park it or drop it | The discovery backlog, chats; spikes in a repo | The person decides |
| 3. Shaping | Decisions made, mockups to react to, risks raised (legal, dependencies, privacy), the work split into items, each sized S, M or L | Chats, design canvases, the delivery backlog | Chats propose; the person decides scope |
| 4. Spec | Each item gets a complete /draft prompt: every constraint upfront, what to test, and whether it can run alongside work in another repo | The delivery backlog, "Ready for dev" | Chats |
| 5. Issue | /draft turns the prompt into an issue in Drafted. The person reviews it, adds notes as comments, and moves it to Ready for dev | GitHub | Claude Code, then the person |
| 6. Build | /next builds it on its own branch, with the checks its size calls for | GitHub, the repo | Claude Code |
| 7. Test | Claude Code runs every automated check. The person tests by hand on real devices, then moves the card to Done or sends it back to More to do with feedback | Devices, the board | Claude Code, then the person |
| 8. Release | Tested issues are bundled into a release with a version, notes and a tag | GitHub | The person decides; Claude Code prepares |
| 9. Learn | When an issue comes back to More to do, ask which written rule would have prevented it, and add it to the handbook or the repo | The handbook, the repo | Anyone proposes; the person approves |

Not every opportunity reaches the end, and that's the point of stages 2 and 3: parking or dropping one early is a good outcome.

## Two backlogs

| | Discovery backlog | Delivery backlog |
| --- | --- | --- |
| Holds | Problems and opportunities not yet committed to | Work committed to, split into items |
| Each entry has | Who has the problem, today's workaround, evidence, existing tools, assumptions, experiments | A tool label, a size (S, M, L), legal and dependency notes, and a status |
| Statuses | Open, being explored, parked, dropped, or moved to delivery | To be discussed (with what's left to decide), or Ready for dev (with its complete /draft prompt) |
| Ends when | A decision: solve it (it moves to the delivery backlog), park it or drop it | The item goes on the board as an issue and leaves the backlog |
| Order | By how much the problem matters | By recommended build order, with a visible line between what's needed before a launch and after it |

Tasks a person does outside Claude Code, such as a post or a sign-up, sit in the delivery backlog too, marked as theirs.

## The board

One shared board across repos. Each card shows its repo, and each repo's scripts only touch its own cards.

| Column | Means |
| --- | --- |
| Drafted | Written by /draft, waiting for review |
| Ready for dev | Approved, waiting to be built |
| More to do | Tested and sent back with feedback; built before anything in Ready for dev |
| Building | Being built now |
| Ready for testing | Built and checked; waiting for testing by hand on a device |
| Done | Approved. The next Claude Code run closes the issue |

Moving a card to Done is the approval. An issue that needs a decision gets a "blocked" label and a question, and is skipped until the label is removed.

## Sizes

| Size | What it is | Becomes the next size when | Checks, in order |
| --- | --- | --- | --- |
| **S** | One small change: about 3 files or fewer, not counting tests, the decision log, the changelog, the version file or regenerated files. No new screen, component or page, and no change to data formats, the settings format, design tokens, launch, the local server, privacy or licences | It crosses any of those limits | The builder writes the code and its tests; the quick check; the reviewer, which also checks the tests |
| **M** | One feature, one screen, or one component or style guide page, new or changed | It grows past one feature or screen | Same as S |
| **L** | Several screens, or a change across an app or the design system, that can't usefully be split. Anything that can be split becomes a series instead | Nothing is bigger | The builder writes the code and its tests; the quick check; the test-checker, which adds missing tests; the reviewer, even if the test-checker failed; the full check, once, run by the builder before merging (the test-checker doesn't run it) |

- **Choosing a size:** when unsure between two, take the bigger. An issue with no size gets one when /next reads it, with the reason noted on the issue.
- **Sizes only go up** during a build. An upgrade changes the label, notes the reason on the issue once, and switches to the new size's checks.
- **Fix rounds:** at most 2, and every check of the size runs again each round. After that the issue is blocked.
- **Merging:** squash-merged into one commit that references the issue, after the quick check passes again on main. An L also needs the full check.
- **The full check also runs before any version bump or release,** whatever the sizes involved.
- **Bundles:** neighbouring S issues in Ready for dev that touch the same area share one branch and one review, with one commit per issue. Issues from More to do are never bundled, refactors only bundle with refactors, and a blocked issue never joins. If one issue grows to M it stays in the bundle; if one grows to L, the whole bundle takes the L checks.
- **Series:** each issue takes its own size's checks. After the last one merges, one review covers the whole series, and the cards wait in Building until it passes. A series that contains an L also gets the full check in that review. Fixes the series review asks for become one follow-up issue that goes straight to Ready for dev, since it fixes work already approved.
- **Idle work:** tidy-ups and refactor proposals are S or M, never L. Tidy-ups always get the test-checker and the reviewer, whatever their size.

## Commands

The commands live in each repo today. In version 2 of this handbook they move into the plugin and become /enamelware:draft, /enamelware:next and /enamelware:tidy.

| Command | Does |
| --- | --- |
| /draft | Turns a pasted spec into one or more issues in Drafted. Never builds. A paste that is only a spec counts as the go-ahead to draft |
| /next | Builds one issue: More to do first, then Ready for dev. Resumes unfinished work first |
| /next all, /next N | Builds in batches until both columns are empty, or N issues. Never stops to ask: blocked issues are labelled and skipped |
| /tidy | Idle work: test improvements, then refactor proposals filed as Drafted issues |

## Working rules

- **The issue is the handoff.** Everything another session or device needs goes on the issue. Nobody is asked to copy text between devices.
- **Safe to stop.** One branch per issue, checkpoints pushed as work goes, and main only holds finished work. After any interruption, the next run resumes first.
- **Testing is split.** Claude Code runs every automated check itself and never asks the person to run commands. The person only does exploratory testing on devices.
- **Judge a run by its exit code,** not by its last line of output.
- **Commits** are small, reference their issue, and are authored as Enamelware.

## Handing work to Claude Code

- Prompts are complete and ready to paste: the person never edits a prompt by hand.
- Every constraint and thing to watch for is stated upfront, so the plan doesn't need checking.
- Legal, dependency and privacy risks are raised in the chat before anything is drafted.
- Each prompt says whether it can run at the same time as work in another repo, or which must go first.
- Several items for one session are pasted together, separated by a line containing only ===.

## Briefs and reports

- **When a brief is pasted:** check it wasn't cut off; check items already done instead of redoing them; make only the listed edits to hand-written pages, and compare before and after to prove nothing else changed.
- **Reports** are in plain language for a designer, with no code: what changed, what was checked, and what looks wrong.
- **Never invent or estimate a value.** List what wasn't found instead.
