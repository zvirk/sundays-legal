---
title: Sundays — Privacy Policy & Terms of Use
---

# Sundays — Privacy Policy

**Last updated:** May 12, 2026

Sundays is a weekly voice journal. Once a week you have a short call with an AI companion that listens; between calls, you can record voice notes or write quick text notes. This page explains what Sundays collects, where it goes, and what we do — and don't — do with it.

If you have a question that this page doesn't answer, email **[zarnabvirk@gmail.com](mailto:zarnabvirk@gmail.com)**.

---

## What Sundays collects

When you use Sundays, the following gets stored:

- **Audio recordings** — your weekly Sunday call and any voice notes you record between calls. By default these are saved on your phone and synced to our backend (Supabase Storage, private bucket scoped to your account). You can turn off audio retention in Settings → Privacy ("transcript only" mode), in which case the audio file is deleted after transcription and only the text is kept.
- **Handwriting photos** — if you upload a photo of a handwritten journal entry, the image is saved on your phone and synced to our backend (Supabase Storage, private bucket scoped to your account). The image is also sent to Anthropic's Claude vision model for one-time OCR; only the resulting transcript is retained server-side beyond the original.
- **Transcripts** — the text version of what you said, generated automatically (on-device for voice notes, server-side via ElevenLabs for the live weekly call, by Claude vision for handwriting uploads).
- **Quick text notes** — anything you type into the app yourself.
- **Themes, summaries, and pull-quotes** — short pieces of text derived from your transcripts by an AI processor (Anthropic's Claude). These power the Insights tab.
- **Semantic embeddings** — a 1,536-number vector representation of each transcript, computed by OpenAI's `text-embedding-3-small` model. Embeddings power the "Search your mind" chat in Insights by letting us find notes by meaning, not just keyword. Each embedding is generated once when a transcript is created or updated; the original transcript text is sent to OpenAI only for that embedding call.
- **Calendar event titles** (optional) — if you enable "Capture moments after events" in Settings, Sundays reads your iOS Calendar for upcoming personal/social events and sends event titles to Anthropic for a one-pass classification (is this a meaningful moment to prompt about?). Only the title is sent — not attendees, location, or notes. Event content stays on your device.
- **Onboarding choices** — the goals you select, your preferred weekly call slot, and your time zone.
- **Names you mention** — when you say someone's name during a call or note, it's extracted as a tag so you can see who comes up in your weeks. This is just a string of letters; it doesn't link to that person's contact info or any external profile.
- **An anonymous account ID** — Sundays doesn't ask you to sign up with an email or password. Your data is tied to an anonymous identifier provisioned on first launch (via Supabase Auth) and to the Apple ID associated with your TestFlight or App Store install. If you Sign in with Apple, the same anonymous account upgrades to your Apple-linked account so your data follows you across devices.

## What Sundays does NOT collect

- **No analytics or tracking SDKs.** No Mixpanel, no Firebase Analytics, no Amplitude, no third-party telemetry.
- **No ads or advertising identifiers.** Sundays does not use IDFA.
- **No location.** The app does not request or store your location.
- **No contacts.** Names that appear in transcripts come from what you say out loud, not from your phone's contact list.
- **No selling or sharing of your data with advertisers, data brokers, or partners.** We don't have any commercial relationships of that kind.

## Where your data goes

Sundays uses a small set of third-party processors. Each has its own privacy policy, linked below.

| Processor | What it does | Their privacy policy |
|---|---|---|
| **Supabase** | Hosts the database (Postgres) and the private storage buckets where your transcripts, summaries, themes, audio recordings, and handwriting photos live. | [supabase.com/privacy](https://supabase.com/privacy) |
| **ElevenLabs** | Powers the real-time weekly Sunday call: streams your voice in, runs speech-to-text, generates the AI companion's voice. The agent system prompt and your live transcript are sent to ElevenLabs during the call only. | [elevenlabs.io/privacy](https://elevenlabs.io/privacy) |
| **Anthropic** | The Claude language model that summarizes your call, extracts themes and names, OCRs your handwriting photos, classifies calendar events (if you opt in to that feature), generates the verbal reading, and synthesizes answers in the "Search your mind" chat. Transcripts are sent to Anthropic only when you trigger one of those features. | [anthropic.com/legal/privacy](https://www.anthropic.com/legal/privacy) |
| **OpenAI** | Generates the semantic embedding (a list of numbers, no human-readable content) for each transcript so the "Search your mind" chat can find notes by meaning instead of keyword. Embeddings are generated once per note and used by Sundays internally; OpenAI does not retain transcript content beyond the API call per their data policy. | [openai.com/policies/privacy-policy](https://openai.com/policies/privacy-policy) |
| **Apple (StoreKit)** | If you subscribe to a paid tier in the future, Apple handles billing. Apple does not share your real name or email with us. | [apple.com/legal/privacy](https://www.apple.com/legal/privacy/) |

We don't share your data with anyone outside of these processors, and only for the specific purposes above.

## How long we keep your data

Your transcripts, themes, summaries, and audio (if retained) are kept for as long as you have an account.

You can delete everything at any time:

- **Settings → Delete account** — wipes your transcripts, themes, summaries, audio files, voice notes, and account record from our backend. The action is irreversible.
- **Settings → Privacy → Audio retention** — switches future voice notes to transcript-only.

You can also export your data first via **Settings → Export your data**, which produces a JSON file of everything Sundays has stored about you.

If you uninstall the app without deleting your account, the local cache on your device goes away but the cloud-stored data stays. To wipe the cloud copy, use Delete account before uninstalling, or email us with a deletion request.

## Encryption

Data in transit between your phone and our processors is encrypted using standard HTTPS / TLS. Audio and image files in Supabase storage are encrypted at rest by Supabase, scoped to your account via row-level security (no other user can read them, only you and a service-role admin pass). On-device audio and handwriting images are protected by iOS's `complete` file-protection class — files are only decryptable while your phone is unlocked. We do not implement custom application-level encryption beyond what the platform provides; Sundays is therefore exempt from US export-control rules on encryption (`ITSAppUsesNonExemptEncryption = false`).

## Developer access (an honest disclosure)

As the sole developer of Sundays, **Zarnab Virk has administrative access to the Supabase project** that hosts your transcripts, voice notes, themes, and summaries. This means I (Zarnab) could technically view stored data via the Supabase admin dashboard, even though the app's row-level security prevents one user from reading another user's rows.

I do not actively review user data, and I never will except in three narrowly defined cases:
- A specific bug report you send me where the data is necessary to reproduce the issue, and only with your explicit consent.
- A legal compulsion (subpoena, court order) — which I would notify you about wherever permitted.
- A safety review if a transcript is automatically flagged for crisis content and you've opted in to follow-up contact.

**This level of access is similar to most journaling apps on the market.** Day One, Bear, Roam Research, Notion, Apple Journal, and almost every other journaling product have the same property at rest: their teams have administrative access to your stored content. Some say so explicitly in their privacy policy; many don't. True end-to-end encryption — where the developer literally cannot decrypt your data — is incompatible with the AI-powered features Sundays depends on (theme extraction, the verbal reading, the search-your-Sundays chat). Those features require Anthropic to receive plaintext during processing.

A more private mode — where specific notes you mark as "private" are encrypted client-side and bypass all AI features — is on the v2 roadmap. Until then, **if a particular reflection feels too sensitive to share given that I could technically read it, don't share it here.** I'd rather you know than feel surprised later.

## Children's privacy

Sundays is intended for users **13 and older**. The app shows a one-time consent screen on first launch. We do not knowingly collect data from anyone under 13. If you believe a child has used Sundays, email us and we'll delete the account.

## Crisis content

If you describe being in crisis during a call or note, the post-call summary may flag the entry so the app can show you helpline information (988 / 741741 in the US, 116 123 in the UK, 112 in the EU). The flag is stored on your account record. It is **not** reported to anyone, sent anywhere, or used for any purpose other than surfacing the helpline card to you.

Sundays is not a crisis service or a substitute for professional mental-health care.

## Your rights

Depending on where you live, you may have specific rights under privacy laws (GDPR in the EU/UK, CCPA in California, similar laws elsewhere):

- **Access** — see what we have about you (Settings → Export your data).
- **Deletion** — delete everything (Settings → Delete account).
- **Correction** — correct anything that's wrong (rename voice notes, edit name spellings, etc., directly in the app).
- **Portability** — your exported JSON is yours to take wherever.
- **Object to processing** — stop using Sundays at any time; data deletion is in your control.

To exercise any right not covered by an in-app action, email **[zarnabvirk@gmail.com](mailto:zarnabvirk@gmail.com)**.

## Changes to this policy

If this policy changes meaningfully, we'll update the "Last updated" date at the top and surface a notice in-app the next time you open Sundays. Material changes (new processors, expanded data collection) will require your opt-in before taking effect on your account.

## Contact

Sundays is built by Zarnab Virk. For privacy questions, deletion requests, or anything else legal-related:

📧 **[zarnabvirk@gmail.com](mailto:zarnabvirk@gmail.com)**

---

# Sundays — Terms of Use

**Last updated:** May 19, 2026

These Terms of Use ("Terms") govern your use of the Sundays mobile application ("Sundays," "the App," "we," "us"). By creating an account or using Sundays, you agree to these Terms. If you do not agree, please do not use Sundays.

## 1. Eligibility

You must be at least 13 years old to use Sundays. If you are between 13 and 18, you represent that you have your parent or guardian's permission to use the App. Sundays is not directed at children under 13, and we do not knowingly collect information from them — see the Children's privacy section in the Privacy Policy above.

## 2. The Service

Sundays is a journaling app built around a once-a-week voice conversation with an AI agent. The App records, transcribes, summarizes, and surfaces long-term patterns from what you share. Specific features may evolve over time.

## 3. Your Content

Everything you record, write, or upload in Sundays — voice notes, transcripts, text entries, handwriting images — is yours. You retain all rights to it.

By using the App, you grant Sundays a limited, non-exclusive license to process your content solely to provide the Service: transcribe audio, generate summaries, extract themes, and surface insights back to you. We do not use your content to train machine-learning models, and we do not share it with third parties except the infrastructure providers necessary to deliver the Service (disclosed in the Privacy Policy above).

## 4. Subscriptions

### Trial and renewal

Sundays is a paid subscription with a 30-day free introductory trial. After the trial, your selected tier renews automatically at the price displayed in the App at the time of purchase (currently $7.99 USD/month or $69.99 USD/year), unless you cancel.

### How billing works

Payment is charged to your Apple ID account at confirmation of purchase. Subscriptions automatically renew at the end of each period unless auto-renew is turned off at least 24 hours before the end of the current period. The account is charged for renewal within 24 hours before the end of the current period. You can manage and cancel subscriptions in your Apple ID's Subscriptions settings.

### Refunds

Subscription refunds are handled by Apple under their standard refund policy. Requests can be submitted at [reportaproblem.apple.com](https://reportaproblem.apple.com). Sundays does not issue refunds directly.

### Free-trial eligibility

The introductory free trial is available once per Apple ID per subscription group. Subsequent re-subscriptions — including after cancellation — may not be eligible for another free trial; Apple determines eligibility.

## 5. AI and professional care

Sundays uses AI (third-party speech and language models, disclosed in the Privacy Policy) to power the conversation, the transcription, and the insights it surfaces. The AI agent is not a therapist, counselor, doctor, or mental-health professional, and Sundays is not a substitute for professional mental-health care, diagnosis, or treatment.

If you are in crisis or considering harming yourself or others, please contact emergency services or a qualified professional immediately. AI-generated content can be inaccurate, incomplete, or out of context. Do not rely on Sundays for medical, psychological, legal, financial, or other professional advice.

## 6. Acceptable use

You agree not to use Sundays to:

- Violate any law or the rights of any third party.
- Share content that is illegal, infringing, harassing, or fraudulent.
- Attempt to reverse-engineer, scrape, or otherwise access non-public parts of the Service.
- Use the Service to build a competing product.

## 7. Termination

You may delete your account at any time from within the App (Settings → Delete account). Account deletion permanently removes your data from Sundays' servers, subject to the retention details in the Privacy Policy above.

We may suspend or terminate your access if you materially breach these Terms. If we terminate your account for breach, no refunds will be issued.

## 8. Intellectual property

The Sundays name, app, design, and software are owned by Zarnab Virk. You may not copy, modify, or redistribute the App or its content except as permitted by these Terms and applicable law.

## 9. Disclaimer of warranties

Sundays is provided "as is" and "as available," without warranties of any kind, express or implied, including merchantability, fitness for a particular purpose, or non-infringement. We do not warrant that the Service will be uninterrupted, error-free, or secure.

## 10. Limitation of liability

To the maximum extent permitted by law, Zarnab Virk and Sundays will not be liable for any indirect, incidental, special, consequential, or punitive damages — including loss of data, loss of revenue, or emotional distress — arising out of or related to your use of the Service. Total liability for any claim relating to the Service will not exceed the amount you have paid to Sundays in the twelve months preceding the claim.

Some jurisdictions do not allow the exclusion or limitation of certain warranties or liabilities, so the limitations above may not apply to you.

## 11. Indemnification

You agree to indemnify and hold harmless Zarnab Virk and Sundays from any claim or demand arising from your breach of these Terms or your misuse of the Service.

## 12. Governing law

These Terms are governed by the laws of the State of New York, United States, without regard to its conflict-of-laws principles. Any dispute will be resolved in the state or federal courts located in New York County, New York, and you consent to the jurisdiction of those courts.

## 13. Changes to these Terms

We may update these Terms from time to time. If a change is material, we will notify you within the App or by email before the change takes effect. Continued use of the Service after the effective date constitutes acceptance.

## 14. Contact

Questions about these Terms can be sent to:

📧 **[zarnabvirk@gmail.com](mailto:zarnabvirk@gmail.com)**
