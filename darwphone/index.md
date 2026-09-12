---
layout: default
title: Darwvin Softphone Privacy Policy
---

# Darwvin Softphone Privacy Policy

Effective date: 2026-09-12

Darwvin Softphone is a SIP softphone. The app is designed to keep user data local except where network communication is required to provide SIP, media, push, provisioning, diagnostics requested by the user, or user-requested sharing.

## Data Darwvin Softphone processes

### SIP and PBX account data
Darwvin Softphone stores SIP server details, usernames, SIP passwords, realms, outbound proxies, TURN credentials, and account preferences in app-private storage. The persisted account data is encrypted with AES-256-GCM using a key held by Android Keystore.

Account data is used to communicate with the SIP/PBX, STUN, and TURN services selected by the user or their provider. Credentials are not sent to a Darwvin-operated backend by this build.

### Calls and media
Voice and video media are exchanged with the user's configured SIP/media infrastructure and remote call participants. Darwvin Softphone does not upload call audio or video to a Darwvin-operated server.

Call recordings are optional, require an explicit in-app confirmation before recording begins, and are stored in app-private local storage. Users can select a recording retention policy (30 days, 90 days, 1 year, or Forever), delete recordings manually, or clear app data. Users can explicitly share a recording through Android's system share sheet.

### Call history
Darwvin Softphone keeps a local history of SIP calls made or received through the app. The database is app-private and bounded to the most recent 1,000 entries. Users can clear this history from the app.

### Contacts
If the user grants Contacts permission, Darwvin Softphone reads device contacts locally to help identify and dial contacts. The current app code does not upload the device address book to a Darwvin-operated service.

### Push notifications
When Firebase Cloud Messaging is configured, Google/Firebase provides an FCM registration token. Darwvin Softphone stores that token locally and may include it in RFC 8599 SIP Contact parameters sent to the user's configured SIP registrar so the registrar can request a wake-up for an incoming call. Firebase/Google and the user's SIP provider process data under their own terms and privacy policies.

Firebase push support is optional; direct SIP operation does not require Darwvin to operate a push backend.

### QR provisioning and deep links
QR provisioning uses Google Code Scanner from Google Play services. Darwvin Softphone parses provisioning data locally. External deep links are not permitted to carry SIP or TURN passwords; credential-bearing provisioning is limited to explicitly scanned or local provisioning input.

### Diagnostics
Darwvin Softphone can collect a bounded in-memory SIP diagnostic trace when Developer Mode is enabled. The app attempts to redact authorization headers, secrets, tokens, SRTP inline keys, digest responses, and SIP user-parts before trace data is stored or exported. Diagnostic exports are created only when the user chooses to share them.

SIP Doctor may perform DNS resolution and TCP/TLS connectivity checks against servers configured by the user.

## Android permissions

Darwvin Softphone may request:
- Microphone, for audio calls.
- Camera, for SIP video calls. QR scanning itself uses Google Code Scanner and does not require Darwvin Softphone to access QR camera frames directly.
- Contacts, for local contact integration.
- Notifications, for incoming and ongoing call notifications.
- Bluetooth nearby-device access where required by Android for Bluetooth call routing.

Permissions can be denied or revoked through Android settings. Features depending on a denied permission may be unavailable.

## Advertising and analytics

The current Darwvin Softphone codebase does not include an advertising SDK or a Darwvin-operated analytics backend.

## Data retention

- Encrypted SIP account data: until the account is removed or app data is cleared.
- Call history: up to 1,000 local entries, until cleared.
- Call recordings: according to the user-selected retention policy (30 days, 90 days, 1 year, or Forever), unless deleted sooner or app data is cleared.
- FCM token: until replaced by Firebase or app data is cleared.
- Developer SIP trace: bounded local/in-memory diagnostic data while Developer Mode is enabled; exported only by explicit user action.
- SIP instant messages: the current implementation keeps a bounded in-memory session list and does not persist a chat archive.

## Data sharing

Darwvin Softphone shares data only as needed with:
- the SIP/PBX, STUN, and TURN services configured by the user or provider;
- Firebase Cloud Messaging when push is enabled;
- Google Play services for the code-scanner component;
- destinations explicitly selected by the user through Android sharing.

Darwvin Softphone does not sell user data.

## Security

Persisted SIP credentials use Android Keystore-backed authenticated encryption. Android app-private storage is used for call history and recordings. TLS/SRTP options are available for compatible SIP providers. No security mechanism can guarantee absolute protection.

## Changes

Material changes to this policy will update the effective date and should be published before or alongside the corresponding app release.

## Contact

Darwvin Softphone is published by **darwvin-dev / Darwvin**. For privacy or support inquiries, contact **darwvindev@gmail.com**.
