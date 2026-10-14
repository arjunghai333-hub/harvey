# Codex instructions for NZ Cricket Store's Harvey fork

## Purpose
Use Harvey as a **Codex-powered B2B lead research and personalised draft assistant** for NZ Cricket Store (https://www.nzcricketstore.com/). Prospecting focus: New Zealand cricket clubs, academies, coaches and school sports coordinators. Prefer targeted, verified, relevant prospects over bulk lead counts.

## Provider and configuration
- Harvey supports Codex directly; see the upstream README section "Using a ChatGPT plan instead (Codex)".
- Keep `brain.provider: codex` and `brain.model: gpt-5.5` unless the maintainer has verified another tool-free model/version. Harvey currently specifies Codex CLI 0.159.3 and ChatGPT sign-in.
- Keep credentials out of Git. Use private environment variables, ignored `.env` and `harvey.local.yaml`.
- Do not assume a ChatGPT sign-in can run unattended indefinitely. Assess credential renewal and licensing/terms before choosing a cloud runtime.
- Do not use a personal Mac as the production runtime. Propose a costed Linux/cloud setup and explain any periodic manual login requirement.

## Safety / operational rules
- Initial mode: **research, enrichment, verified sources, CSV export and email drafts only**.
- No outbound email or automatic LinkedIn messages. Do not enable channels, change zero-send limits, or send communications without explicit user authorisation and a reviewed compliance setup.
- Every prospect should have a real source and clearly labelled contact verification status. Do not invent a business, contact, email or purchase intent.
- Observe NZ Unsolicited Electronic Messages Act, Privacy Act and relevant Australian law if geography expands; publicly available contact details alone do not imply unrestricted marketing consent. Respect opt-outs, suppression lists and source terms.
- Record why each organisation may need cricket equipment. Exclude existing customers/partners where a suppression source is available.
- Draft emails like a real person and don't claim familiarity, affiliation, discounts, shipping promises or stock availability unless verified.

## Implementation checklist
1. Validate project dependencies and run repository tests.
2. Confirm Codex CLI version, authenticated ChatGPT plan and model compatibility, without exposing credentials.
3. Train on `https://www.nzcricketstore.com/` using `harvey train https://www.nzcricketstore.com/ --provider codex --model gpt-5.5`. Review generated product facts and do not blindly overwrite safety settings.
4. Evaluate whether Harvey's OpenStreetMap-centric discovery can find clubs, school cricket coordinators and coaches well. If coverage is poor, propose a source-compliant NZ-specific discovery adapter rather than fabricating leads.
5. Keep `channels.email.enabled: false`, `max_daily_sends: 0`, `require_approval: true` and `channels.linkedin.enabled: false` throughout the initial trial.
6. Create a small, source-verified sample of NZ prospects with relevance scores and personalised **drafts only**.
7. Only after successful local tests, prepare a Mac-independent hosting plan with credential renewal and privacy safeguards.

The repository's `CLAUDE.md` includes older Claude-focused instructions; Codex work should follow this file and current code/README, not assume Claude is required.
