# AGENT FILL-INSTRUCTIONS — Privacy Policy

**Mission:** Fill out the app privacy policy template at `index.html` in this repo, push it, and verify the live page. The final page must be a complete, consistent, store-ready privacy policy for **one specific app** — no placeholders, no leftover template markers, no claims that don't match what the app actually does.

**Repo:** `miladnoo/privacy-policy` (public)
**Live URL after deploy:** `https://miladnoo.github.io/privacy-policy/`

---

## Step 1 — Gather facts before you edit anything

Do NOT invent data practices. You must find out what the app actually does. Sources of truth, in order:

1. Ask the developer (Quiz / Milad) for the app name and any facts below you can't determine yourself. He decides — never guess app identity or contact details.
2. The app's codebase (if accessible): what SDKs are in the dependency manifest, what permissions are declared, whether there's an account/sign-in system, whether there are purchases or subscriptions.
3. If the app is already in a store: Google Play Console "Data safety" answers and App Store Connect "App Privacy" answers **must stay consistent** with this policy. Read them if available.

Fill out this fact sheet before touching the HTML:

| Fact | Answer |
|---|---|
| App display name ({{APP_NAME}}) | |
| One-line description of what the app does ({{APP_DESCRIPTION}}) | |
| Developer entity: legal company name, or "the individual developer" ({{DEVELOPER_ENTITY}}) | |
| Business/legal address ({{DEVELOPER_ADDRESS}}) — or mark N/A and delete the line | |
| Working contact email ({{CONTACT_EMAIL}}) — must be real and monitored | |
| Effective date / Last-updated date (today) | |
| What data is collected automatically ({{AUTO_DATA_DETAILS}}) — device type, OS, app version, usage stats, crash logs, IP, advertising ID? | |
| Exact signup/account fields ({{ACCOUNT_FIELDS}}) — or "no account system" | |
| Payment processors used, if purchases/subscriptions exist ({{PAYMENT_PROCESSOR_LIST}}) | |
| Every third-party SDK in the app ({{THIRD_PARTY_SDK_TABLE}}) with purpose + policy URL | |
| Does the app request device permissions (location, camera, photos, mic, contacts, notifications…)? | Keep or delete §1.4 |
| Does the app show ads? | Keep or delete §6 |
| Does the app support account creation? | Keep or delete §14 |
| Does the app target children under 13? | Keep or rewrite §11 |

---

## Step 2 — Edit `index.html`

1. Open `index.html`. Read the `FILL-OUT CHECKLIST` comment block at the top (it is a duplicate of this sheet; delete the whole block when done).
2. Replace **every** `{{TOKEN}}` with the real value from your fact sheet. Replace the token text itself, inside the braces. If a value is long (like the SDK table), replace the whole placeholder including surrounding markup as instructed below.
3. **Conditional sections** — keep ONLY the ones that match the app, delete the rest entirely (heading + body):
   - `1.4 Device Permissions and Sensitive Information` — keep only if the app actually requests sensitive permissions; if kept, replace the `{{PERMISSION_1_PURPOSE}}`/`{{PERMISSION_1_TRIGGER}}` bullet with one bullet **per permission** actually requested.
   - `6. Advertising` — keep only if the app shows ads.
   - `14. Account Deletion` — keep only if the app has accounts. **Important:** Apple rejects apps that support account creation but offer no in-app account-deletion option — if accounts exist, keep this section and fill `{{ACCOUNT_DELETION_PATH}}` with the actual path (e.g., "Settings → Account → Delete Account").
   - `11. Children's Privacy` — if the app is directed at children, replace the default paragraph with a parental-consent section (and make sure Google Play's "Data safety" declares child-directed content / COPPA where relevant).
4. **Section 5 SDK table:** replace the placeholder row inside `<tbody>` with one real row per SDK the app embeds. Every SDK you find in the app's dependency manifest belongs here: analytics (Firebase/GA4, Mixpanel), crash (Firebase Crashlytics, Sentry), ads (AdMob etc.), payments (RevenueCat, Stripe), auth (Firebase Auth, Sign in with Apple/Google), attribution (AppsFlyer, Branch), etc. Each row: SDK name | what it does | link to its own privacy policy. If the app embeds NO third-party SDKs, delete the table and say so in plain text.
5. Leave all legal-structure text (GDPR/CCPA/retention/security sections) intact — do not trim required sections to shorten the document.

---

## Step 3 — Verification checklist (run before committing)

- [ ] `grep -n "{{" index.html` returns **nothing** (no leftover placeholders)
- [ ] `grep -n "DELETE IT ENTIRELY\|KEEP THIS SECTION" index.html` returns nothing (no leftover editor comments)
- [ ] App name, dates, email, and entity are correct and spelled consistently throughout
- [ ] Every SDK named in the app is in the §5 table, and the table lists nothing that isn't in the app
- [ ] The policy's claims match the store privacy forms (Google Play Data safety, Apple App Privacy) and the app's real permission list
- [ ] Contact email is the real one — not a template address
- [ ] Effective/last-updated dates are today's date
- [ ] If accounts exist → §14 present; if ads → §6 present; if permissions → §1.4 present
- [ ] File is valid HTML (opens cleanly in a browser, no broken tags)

---

## Step 4 — Commit, push, verify live

```bash
git add index.html
git commit -m "Fill in privacy policy for <APP NAME>"
git push origin main
```

Then verify the deployment (GitHub Pages builds in ~1 min):

```bash
curl -sI https://miladnoo.github.io/privacy-policy/ | head -5          # expect 200
curl -s  https://miladnoo.github.io/privacy-policy/ | grep -c "{{"     # expect 0
```

Report back: the app name, the live URL, and confirmation that the page contains zero placeholders.

---

## Hard rules

- **Do not fabricate** data collection, SDKs, a company name, an address, or an email. If you cannot determine a fact, ask the developer. A privacy policy that lies is worse than one that is incomplete.
- Do not remove required structural sections (GDPR rights, CCPA, retention, security, contact) to make it shorter.
- This template is general legal guidance, not legal advice. Do not claim it was reviewed by a lawyer.
- Never commit credentials or internal notes; the repo is public.
- Only edit `index.html` in this repo — do not touch other repos, and do not publish the policy anywhere except this GitHub Pages site unless told to.

## Store requirement quick reference (why these sections exist)

- **Google Play:** any app that handles personal/sensitive user data must provide a privacy policy URL in Play Console (App content → Privacy policy), and the Data safety declarations must match the policy and every shipped SDK. Permissions requesting sensitive data may trigger extra review.
- **Apple App Store:** apps that collect data must have a privacy policy URL in App Store Connect and (if the app collects data) include a link inside the app; apps that support account creation must provide in-app account deletion; App Privacy "nutrition labels" must match the policy.
- **Law:** GDPR/UK-GDPR rights for EEA/UK/Swiss users; CCPA/CPRA rights for California residents; COPPA if directed at children under 13.
