---
name: design
description: Enamelware's design principles, accessibility standard and how tools use Enamel. Use when designing, building or reviewing anything users see: screens, components, layout, focus, motion, colour, type, contrast, touch targets, controller hints, text entry, or a mockup. Enamel's DESIGN.md holds the tokens and components themselves.
---

# Design

Every Enamelware tool is styled with Enamel, the shared design system. This skill holds the principles and rules all tools share; Enamel's [DESIGN.md](https://github.com/enamelware/enamel/blob/main/DESIGN.md) and style guide hold the tokens, components and their values, and win on any detail.

## Design principles

1. **Feels like SteamOS, never copied from it.** Gaming Mode's look and behaviour are the baseline; Kettle shows through one accent colour. Nothing is taken from Valve or the Steam client: no CSS, assets, logos or screenshots.
2. **Controller first, any screen.** Everything works with a controller alone, on x86 and ARM. Layouts are fluid and never tied to a screen size, device or aspect ratio; devices are for testing, not layout targets. Nothing needs a terminal in Gaming Mode.

## Enamel first

- Every screen is built from Enamel's components and tokens before any new CSS is written.
- When Enamel lacks something, the gap is filed and fixed in Enamel, never styled inside an app.
- Enamel's [DESIGN.md](https://github.com/enamelware/enamel/blob/main/DESIGN.md) holds the detailed rules: tokens, the spacing grid, sizing and scaling, type, focus, motion and accents. Its style guide shows them live.

## Accessibility

WCAG 2.2 at level AA is the floor. These are the parts that matter most for a controller-first app on a handheld; the numbers in brackets are the success criteria, for looking up the detail.

- **Focus is always visible and never covered.** A hint bar, action bar, toast or overlay never hides the focused item (2.4.7, 2.4.11). Aim for it to be fully visible, not just partly (2.4.12).
- **A strong focus ring:** at least 2 CSS pixels thick, with 3:1 contrast against what's next to it (2.4.13).
- **Enough contrast:** body text at least 4.5:1 against its background, large text 3:1, and buttons, borders and focus rings 3:1 (1.4.3, 1.4.11). On dark surfaces, also check with APCA, which judges light-on-dark contrast more accurately: aim for Lc 75 for body text, Lc 60 for larger text and Lc 45 for UI elements such as focus rings. WCAG 2.2 stays the floor; APCA's thresholds are still a draft and can change.
- **Never colour alone.** States such as selected, missing or new always carry a word or an icon as well as a colour (1.4.1).
- **Text can grow.** Text can be enlarged to 200% without being cut off or overlapping (1.4.4), so system UI scale and text-size settings work.
- **Touch targets big enough:** at least 24×24 CSS pixels, aiming for 44×44 (2.5.8, 2.5.5).
- **Motion that stops.** Anything that moves on its own for more than 5 seconds stops by itself or can be paused (2.2.2). With reduced motion on, non-essential movement is removed (2.3.3).

Sources: [WCAG 2.2](https://www.w3.org/TR/WCAG22/) and [What's new in WCAG 2.2](https://w3.org/WAI/standards-guidelines/wcag/new-in-22/) (W3C), and the [APCA introduction](https://github.com/Myndex/apca-introduction) by its author.

## Feels native on a Steam Deck

Enamelware tools aren't sold on Steam, but Valve's compatibility review is the clearest written bar for feeling native in Gaming Mode.

- **Everything works with the controller alone,** with default controls, and nothing needs a setting changed first.
- **Hints match the input in use:** controller buttons while a controller is used, never keyboard or mouse prompts.
- **Text entry without a keyboard:** any text field works with the controller, through a built-in entry or a clear hint to open Steam's on-screen keyboard.
- **Readable at arm's length:** the smallest text meets Valve's bar (at least 9 pixels tall on the Steam Deck's own screen), aiming for 12. Check it by hand in screenshots from each test device at its own resolution. It's a readability check, never a layout target, so no size is written into code, styles or tests.
- **No mouse-only moments:** every launcher, dialog and error screen works with the controller.
- **Smooth by default:** responsive without tuning, including on slower ARM devices.

Source: [Steam Deck compatibility review](https://partner.steamgames.com/doc/steamdeck/compat) (Steamworks).

## Where the details live

| For | Read |
| --- | --- |
| Tokens, components, grid, sizes, type, focus, motion, accents | Enamel's [DESIGN.md](https://github.com/enamelware/enamel/blob/main/DESIGN.md) |
| Seeing components live | Enamel's style guide |
| Web platform support and controller input | [skills/development](../development/SKILL.md) |
