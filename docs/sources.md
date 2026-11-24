# Sources

Where to look before searching the web, and how much weight each source carries. The skills hold the distilled rules; go to a source only when a rule is unclear or a case isn't covered.

## Tiers

| Tier | What counts | Weight |
| --- | --- | --- |
| Official | Platform owners and standards bodies: Valve, W3C, MDN, Flathub, Anthropic, GitHub, the Python and mpv projects, licence stewards | Wins over everything below, but never over a recorded decision |
| Trusted | Named experts and established publications whose work has held up, chosen one by one | Used when official sources are silent or unclear |
| Opinion | Blogs and posts that are useful but personal | Ideas only, never a rule on their own; marked as opinion wherever they are cited |

## Sources by area

| Area | Source | Tier | Use it for |
| --- | --- | --- | --- |
| Design | [WCAG 2.2](https://www.w3.org/TR/WCAG22/) and [What's new in 2.2](https://w3.org/WAI/standards-guidelines/wcag/new-in-22/) | Official | Accessibility floor: focus, contrast, target size, motion |
| Design | [Steam Deck compatibility review](https://partner.steamgames.com/doc/steamdeck/compat) | Official | What "feels native on a Deck" means: controller, hints, text size, on-screen keyboard |
| Design | [APCA introduction](https://github.com/Myndex/apca-introduction) | Trusted | A second contrast check on dark surfaces |
| Design | Anthropic's frontend-design skill | Trusted | Visual craft guidance when building interface; never over Enamel's own rules |
| Development | [MDN Web Docs](https://developer.mozilla.org/) | Official | How HTML, CSS and JavaScript behave, and browser support |
| Development | [Flathub requirements](https://docs.flathub.org/docs/for-app-authors/requirements) and [MetaInfo guidelines](https://docs.flathub.org/docs/for-app-authors/metainfo-guidelines) | Official | App IDs, permissions, metadata, if a tool ships as a Flatpak |
| Development | Python documentation and PEP 8 | Official | The standard library and code style |
| Development | The mpv manual | Official | Playback, scripting, on-screen controls |
| Development | SPDX licence list and the GPL FAQ | Official | Licence identifiers, headers, compatibility |
| Operations | Claude Code documentation | Official | Commands, skills, subagents, hooks, settings, plugins; checked before building any of them |
| Operations | GitHub documentation | Official | Issues, Projects, Actions, Pages |

## Websites and authors called out by name

Specific websites and authors Enamelware has chosen to follow, with the tier they carry.

| Website or author | Area | Tier | Use it for |
| --- | --- | --- | --- |
| Birgitta Böckeler, [Exploring Gen AI series](https://martinfowler.com/articles/exploring-gen-ai.html) on martinfowler.com (Thoughtworks), starting with [Context Engineering for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html) | Operations | Trusted | How context is structured and loaded for coding agents |
| Gregory Muryn-Mukha, [Your AI agent can read your codebase. It doesn't know your product.](https://uxdesign.cc/your-ai-agent-can-read-your-codebase-it-doesnt-know-your-product-b5ea0cd77989) (UX Collective) | Product | Opinion | How to capture product context agents can't infer from code |

## How sources are used

- **Rules first, sources second.** Go to a source only when a rule is unclear or a case isn't covered.
- **Platform facts are checked, not remembered.** SteamOS, SteamOS-like OSes and Steam hardware change quickly: check current official sources before relying on a fact about them.
- **Cite what a decision rests on.** A decision log entry that depends on a source links to it, with the date it was checked.
- **Adding a source** means a row here with its tier and what it's for; a website or author called out by name goes in the called-out table. A source with no row is opinion until someone adds it.
