---
name: development
description: Enamelware's development standards. Use when writing, reviewing, testing or refactoring code, choosing a web or Python feature, handling controller input, preparing a Flatpak, committing, or checking a fact about SteamOS, SteamOS-like OSes or Steam hardware.
---

# Development

These standards apply to every Enamelware repo. A repo's CLAUDE.md adds what's specific to it; its recorded decisions win where the two differ.

## Facts

- **Check platform facts, don't remember them.** SteamOS, SteamOS-like OSes and Steam hardware change quickly: check current official sources before relying on a fact about them, and name the device a measurement was taken on.
- **Never invent or estimate a value.** List what wasn't found instead.

## Code and dependencies

- Plain HTML, CSS and JavaScript as ES modules: no frameworks and no build step. Python uses the standard library.
- Everything runs on x86 and ARM, so no compiled dependencies.
- A new dependency is a hard stop ([skills/decisions](../decisions/SKILL.md)). Nothing gets installed on a device without asking.
- The core logic stays independent of the interface. Settings and data are plain JSON.
- Every new file carries an SPDX licence header for its repo's licence.

## Web platform

- **Check browser support first.** Before using a newer HTML, CSS or JavaScript feature, check MDN's compatibility table: it must work in the browser engine the tool runs in, on the target devices, with no flags. Each repo's CLAUDE.md names that engine.
- **Real elements for real things.** Buttons are buttons and lists are lists, so focus, screen readers and browser defaults work without extra code.
- **Input arrives as keys.** Steam Input maps the controller to keys and the app listens for those. The Gamepad API is used only where a repo's recorded decision says so.

Sources: [MDN Web Docs](https://developer.mozilla.org/), in particular [:focus-visible](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible), [prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion) and the [Gamepad API](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API).

## Testing

- **Claude Code runs every automated check.** A person is never asked to run commands; people only test by hand on devices.
- **The builder writes the tests.** A test counts only if it would fail when the feature breaks.
- **Pure logic is built test-first** from sample inputs.
- **Judge a run by its exit code,** not by its last line of output.
- **Never run the same check twice** on the same code.
- **Refactors keep behaviour the same,** and never loosen or remove a test.
- **Sample content is invented.** Test files, titles and names never come from anyone's real library.

## Git

- Small commits that reference their issue. Tracked files are deleted with git rm.
- Never force-push, and never move a pushed tag: a mistake is fixed by releasing the next version.
- Every real decision goes in the repo's decision log, dated, with the reason.
- One command at a time, so each matches the repo's permission rules.

## Flatpak and Flathub

These apply once a tool ships as a Flatpak; the first two shape names and permissions earlier.

- **An app ID you can prove:** a reverse domain name, ideally for a domain Enamelware owns, matching the ID in the MetaInfo file exactly.
- **The fewest permissions possible:** portals and standard folders; media folders read-only where possible, never the whole home folder.
- **A valid MetaInfo file** that passes Flathub's linter, with an SPDX licence, a metadata licence, an age rating, screenshots and a desktop file.
- **Names that respect trademarks:** no "Steam" in any app name or icon.
- **Builds work offline:** nothing is downloaded during a build, and runtimes come from Flathub.

Sources: [Flathub requirements](https://docs.flathub.org/docs/for-app-authors/requirements) and [MetaInfo guidelines](https://docs.flathub.org/docs/for-app-authors/metainfo-guidelines).
