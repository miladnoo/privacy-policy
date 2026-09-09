# Privacy Policy (template + hosted page)

A self-contained, fill-in privacy policy template for a mobile app, hosted on GitHub Pages at:

**https://miladnoo.github.io/privacy-policy/**

## Files

| File | Purpose |
|---|---|
| `index.html` | **The template — this is the file you fill out.** A complete privacy policy with `{{PLACEHOLDERS}}` to replace and conditional sections to keep or delete. Live on GitHub Pages from the `main` branch. |
| `AGENT-FILL-INSTRUCTIONS.md` | Step-by-step brief for an agent (or human) that fills the template: fact sheet, edit rules, verification checks, deploy steps. |

## How to fill it out

1. Read `AGENT-FILL-INSTRUCTIONS.md` first — it lists every fact you need to gather (app name, contact email, SDK list, etc.).
2. Open `index.html`, replace every `{{TOKEN}}`, delete the conditional sections that don't apply to the app (marked with HTML comments), and fill the third-party SDK table with the SDKs the app actually embeds.
3. Delete the `FILL-OUT CHECKLIST` comment block at the top.
4. Check nothing is left: the page should contain zero `{{` and zero `DELETE IT ENTIRELY` comments.
5. Commit + push to `main` — the live page updates automatically (~1 min).

## Notes

- Template structure is original and written to line up with what Google Play and the Apple App Store actually check (privacy policy URL, Data safety / App Privacy consistency, account deletion, GDPR/CCPA/COPPA coverage). Store requirements are summarized in the instructions file.
- General information, **not legal advice**. Have a lawyer review before publishing if the stakes are high.
