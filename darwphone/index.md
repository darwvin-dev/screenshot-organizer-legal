---
layout: default
title: DarwPhone Privacy Policy
---

# DarwPhone Privacy Policy — release draft

Effective date: 2026-09-07

DarwPhone is a SIP softphone. The app is designed to keep user data local except where network communication is required to provide SIP, media, push, provisioning, or user-requested sharing.

## Data DarwPhone processes

### SIP and PBX account data
DarwPhone stores SIP server details, usernames, SIP passwords, realms, outbound proxies, TURN credentials, and account preferences in app-private storage. The persisted account blob is encrypted with AES-256-GCM using a key held by Android Keystore.

Account data is used to communicate with the SIP/PBX, STUN, and TURN services selected by the user or their provider. Credentials are not sent to a DarwPhone-operated backend by this build.

### Calls and media
Voice and video media are exchanged with the user's configured SIP/media infrastructure and remote call participants. DarwPhone does not upload call audio or video to a DarwPhone-operated server.

Call recordings are optional, require an explicit in-app confirmation before recording begins, and are stored in app-private local storage until the user deletes them or clears app data. Users can explicitly share a recording through Android's system share sheet.

### Call history
DarwPhone keeps a local history of DarwPhone SIP calls. The database is app-private and is bounded to the most recent 1,000 entries. Users can clear this history from the app.

### Contacts
If the user grants Contacts permission, DarwPhone reads device contacts locally to help identify and dial contacts. The current app code does not upload the device address book to a DarwPhone-operated service.

### Push notifications
When Firebase Cloud Messaging is configured, Google/Firebase provides an FCM registration token. DarwPhone stores that token locally and may include it in RFC 8599 SIP Contact parameters sent to the user's configured SIP registrar so the registrar can request a wake-up for an incoming call. Firebase/Google and the user's SIP provider process data under their own terms and privacy policies.

### QR provisioning and deep links
QR provisioning uses Google Code Scanner from Google Play services. DarwPhone parses provisioning data locally. External deep links are not permitted to carry SIP or TURN passwords; credential-bearing provisioning is limited to explicitly scanned/local provisioning input.

### Diagnostics
DarwPhone can collect an in-memory SIP diagnostic trace when Developer Mode is enabled. The app attempts to redact authorization headers, secrets, tokens, SRTP inline keys, digest responses, and SIP user-parts. Diagnostic exports are created only when the user chooses to share them.

The SIP Doctor may perform DNS resolution and TCP/TLS connectivity checks against servers configured by the user.

## Android permissions

DarwPhone may request:
- Microphone, for audio calls.
- Camera, for SIP video calls. QR scanning itself uses Google Code Scanner and does not require DarwPhone to access camera frames directly.
- Contacts, for local contact integration.
- Notifications, for incoming and ongoing call notifications.
- Bluetooth nearby-device access where required by Android for Bluetooth call routing.

Permissions can be denied or revoked through Android settings. Features depending on a denied permission may be unavailable.

## Advertising and analytics

The current DarwPhone codebase does not include an advertising SDK or a DarwPhone-operated analytics backend.

## Data retention

- Encrypted SIP account data: until the account is removed or app data is cleared.
- Call history: up to 1,000 local entries, until cleared.
- Call recordings: until the user deletes them or clears app data.
- FCM token: until replaced by Firebase or app data is cleared.
- Developer SIP trace: in memory while enabled; exported only by explicit user action.
- SIP instant messages: the current implementation keeps a bounded in-memory session list and does not persist a chat archive.

## Data sharing

DarwPhone shares data only as needed with:
- the SIP/PBX, STUN, and TURN services configured by the user/provider;
- Firebase Cloud Messaging when push is enabled;
- Google Play services for the code-scanner component;
- destinations explicitly selected by the user through Android sharing.

DarwPhone does not sell user data.

## Security

Persisted SIP credentials use Android Keystore-backed authenticated encryption. Android app-private storage is used for call history and recordings. TLS/SRTP options are available for compatible SIP providers. No security mechanism can guarantee absolute protection.

## Changes

Material changes to this policy should update the effective date and be published before or alongside the corresponding app release.

## Contact

DarwPhone is published by **darwvin-dev / Darwvin**. For privacy or support inquiries, contact **darwvindev@gmail.com**.
