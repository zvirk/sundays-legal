---
title: Sundays — Privacy Policy
---

# Sundays — Privacy Policy

**Last updated:** May 1, 2026

Sundays is a weekly voice journal. Once a week you have a short call with an AI companion that listens; between calls, you can record voice notes or write quick text notes. This page explains what Sundays collects, where it goes, and what we do — and don't — do with it.

If you have a question that this page doesn't answer, email **[zarnabvirk@gmail.com](mailto:zarnabvirk@gmail.com)**.

---

## What Sundays collects

When you use Sundays, the following gets stored:

- **Audio recordings** — your weekly Sunday call and any voice notes you record between calls. By default these are saved on your phone and synced to our backend. You can turn off audio retention in Settings → Privacy ("transcript only" mode), in which case the audio file is deleted after transcription and only the text is kept.
- **Transcripts** — the text version of what you said, generated automatically (on-device for voice notes, server-side via ElevenLabs for the live weekly call).
- **Quick text notes** — anything you type into the app yourself.
- **Themes, summaries, and pull-quotes** — short pieces of text derived from your transcripts by an AI processor (Anthropic's Claude). These power the Insights tab.
- **Onboarding choices** — the goals you select, your preferred weekly call slot, and your time zone.
- **Names you mention** — when you say someone's name during a call or note, it's extracted as a tag so you can see who comes up in your weeks. This is just a string of letters; it doesn't link to that person's contact info or any external profile.
- **An anonymous account ID** — Sundays doesn't ask you to sign up with an email or password. Your data is tied to an anonymous identifier provisioned on first launch (via Supabase Auth) and to the Apple ID associated with your TestFlight or App Store install.

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
| **Supabase** | Hosts the database (Postgres) and audio storage where your transcripts, summaries, themes, and audio files are saved. | [supabase.com/privacy](https://supabase.com/privacy) |
| **ElevenLabs** | Powers the real-time weekly Sunday call: streams your voice in, runs speech-to-text, generates the AI companion's voice. The agent system prompt and your live transcript are sent to ElevenLabs during the call only. | [elevenlabs.io/privacy](https://elevenlabs.io/privacy) |
| **Anthropic** | The Claude language model that summarizes your call, extracts themes and names, generates the verbal reading, and answers your "Ask your past Sundays" chat queries. Transcripts are sent to Anthropic only when you trigger one of those features. | [anthropic.com/legal/privacy](https://www.anthropic.com/legal/privacy) |
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

Data in transit between your phone and our processors is encrypted using standard HTTPS / TLS. Audio files in Supabase storage are encrypted at rest by Supabase. Voice-note audio on your device is protected by iOS's `complete` file-protection class — files are only decryptable while your phone is unlocked. We do not implement custom application-level encryption beyond what the platform provides; Sundays is therefore exempt from US export-control rules on encryption (`ITSAppUsesNonExemptEncryption = false`).

## Developer access (an honest disclosure)

As the sole developer of Sundays, **Zarnab Virk has administrative access to the Supabase project** that hosts your transcripts, voice notes, themes, and summaries. This means I (Zarnab) could technically view stored data via the Supabase admin dashboard, even though the app's row-level security prevents one user from reading another user's rows.

I do not actively review user data, and I never will except in three narrowly defined cases:
- A specific bug report you send me where the data is necessary to reproduce the issue, and only with your explicit consent.
- A legal compulsion (subpoena, court order) — which I would notify you about wherever permitted.
- A safety review if a transcript is automatically flagged for crisis content and you've opted in to follow-up contact.

This level of developer access is the standard model for solo-developed journaling apps at this stage (Day One, Bear, Roam, Notion, and most others have the same property, even when not explicitly stated in their policies). True end-to-end encryption — where the developer literally cannot decrypt your data — is incompatible with the AI-powered features Sundays depends on (theme extraction, the verbal reading, the search-your-Sundays chat). Those features require Anthropic to receive plaintext during processing.

If this trade-off doesn't work for you, **don't use Sundays for content you wouldn't be comfortable with me being able to read.** I'd rather you know than feel surprised later.

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
