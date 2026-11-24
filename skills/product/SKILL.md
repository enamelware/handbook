---
name: product
description: Enamelware's product principles, positioning, voice, interaction principles and self-test. Use when shaping or speccing a feature, writing any text users read, deciding how a control or screen behaves, naming an app or anything users see, writing public text about a tool, or checking whether an idea fits what Enamelware does and doesn't do.
---

# Product

Every Enamelware tool follows these principles. A feature that breaks one needs a reason recorded in that repo's decision log.

## Product principles

1. **One app, one job.** Small separate apps instead of one that does everything. For example, video and audio are deliberately split.
2. **The user's files are theirs.** Tools read the user's media and never move, rename, create or write to it.
3. **Never online by itself.** No scraping, no online metadata, no automatic requests. A tool goes online only when the user asks it to, such as checking for updates.
4. **Fail safe and explain.** A missing dependency is detected and explained. A failed scan or update never stops a tool from opening. No silent failures.
5. **Open, without locking in.** Open source. Plain HTML, CSS and JavaScript with no frameworks or build step; standard-library Python; dependencies only when they earn their place; settings and data in plain JSON.
6. **Shared foundations, one direction.** Apps depend on Enamel and the shared workflow, never the other way round. A gap is fixed upstream in Enamel, not styled inside an app. Renaming anything shared means reporting what would break first.
7. **Public by default, private by rule.** Repos are written to be read by anyone, in the project voice ("Enamelware uses…"). Example content is always invented, never a near copy of a real title. Nothing from a person's own devices, library or accounts is ever published: no file names, paths, screenshots or logs.

## Naming

- Apps are named Kettle plus their medium, with no verbs: Kettle Video, not Kettle Watch.
- No name, icon or description uses someone else's trademark: never "Steam" in a name, even descriptively. Public material says Enamelware is not affiliated with Valve.
- A new name is a hard stop (see [skills/decisions](../decisions/SKILL.md)): it needs checks on the GitHub handle, domain, app store IDs and trademarks before it's used.

## Who the tools are for

People who play and watch on a SteamOS-style handheld or a PC under the TV, and who keep their own films, music and games. They want each thing to just work from the couch with a controller, without accounts, setup sessions or a media centre to manage. Enamelware tools are for players, not gamers: calm, useful and unshowy.

## What Enamelware is not

- **Not a media centre.** No all-in-one app like Kodi: each tool does one job and stays small.
- **Not a service.** No accounts, sign-ins, ads, tracking or cloud.
- **Not a scraper.** No artwork, ratings or metadata pulled from the internet: what the user sees comes from their own files.
- **Not a Steam add-on.** Tools sit beside Steam and feel like part of it, but never modify Steam or depend on its private parts.

## Voice

- **Plain, short and calm.** Words a first-time user understands without reading twice. No jargon, no exclamation marks, no gamer slang.
- **Buttons say what they do:** Play, Quit, Menu, Rescan. Never a vague "OK" when a verb fits.
- **States are named, not hidden:** "Missing", "2 parts", "Beta". The user is never left guessing why something looks different.
- **Errors say what happened and what to do next,** where it happened, in one or two sentences.
- **Public text** uses the project voice ("Kettle Video shows…"), never "I" or "we".

## Interaction principles

- **A does the main thing at once.** Choosing a film plays it, and resumes it if it can. Extra options come later and on another button, never in the way.
- **B always goes back.** On a tool's top screen, it opens the menu with Quit already selected: leaving is quick, but always explicit. No double presses, no hidden gestures.
- **Things happen when the user asks.** Rescans, updates and online checks start from a user action, never by themselves in the background.
- **Nothing is lost by surprise.** The tool never deletes anything on its own; things that disappear stay listed as Missing until the user removes them. Actions that can be undone need no confirmation.
- **Feedback without interruption.** Progress and results appear as a brief message in a corner, like Steam's own notifications, never as a dialog that blocks the screen.
- **Few options, good defaults.** A setting exists only when people genuinely want different things. Menus are short, and their rows need no descriptions.
- **Long lists stay fast to scan.** Lists over grids for big collections, with quick jumps through them.

## Self-test

Before shipping anything users see, answer yes to all of these:

1. Does it feel like it belongs in Gaming Mode?
2. Can it be done with the controller alone, without reading instructions?
3. Is it obvious how to go back, and how to leave?
4. Does it stay within the tool's one job?
5. Does it work offline, and does nothing happen that the user didn't ask for?
6. Are the user's files exactly as they were?
7. Would a first-time user understand every word on the screen?
