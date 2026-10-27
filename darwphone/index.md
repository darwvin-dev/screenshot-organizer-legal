---
layout: default
title: Darwvin Softphone Privacy Policy
---

# Darwvin Softphone Privacy Policy

Effective date: 2026-10-05

Last updated: 2026-10-05 (end-to-end encrypted sync: deletion markers, password changes, synced preferences)

Darwvin Softphone is a SIP softphone for Android and desktop (Windows, Linux, macOS). The app is designed to keep call-related user data local except where network communication is required to provide SIP, media, push, provisioning, diagnostics requested by the user, or user-requested sharing.

Using the app requires a Darwvin account. The account, the free trial, paid plans and app updates are provided by the Darwvin account and license service operated by Darwvin (`api.darwvin.com`), which is described in its own section below. The same account and the same practices apply to the Android and the desktop apps and to the account pages on darwvin.com.

## Darwvin account and license service

### What the service stores
- **Account:** email address, optional name, a bcrypt hash of the password (the password itself is never stored), account creation time, email verification time, and the start and end of the free trial.
- **Devices:** for each device signed in to the account, a device identifier that is a one-way SHA-256 hash of the operating system's device identifier (Android `ANDROID_ID`, or the desktop machine id) prefixed with an app-specific string, or of a random identifier the app creates when none is available. The raw identifier never leaves the device. With it the service stores the device name (phone manufacturer and model, or computer name), platform, app version, sign-in time and last-seen time.
- **Website sign-ins:** for sign-ins on darwvin.com, a hashed session token, the browser's user-agent string and times.
- **Purchases:** for online payments, the plan, amount, currency, payment gateway, the gateway's reference number, status and times; card or bank details are entered only on the payment gateway's own page and never reach Darwvin. For store purchases (Google Play, Cafe Bazaar, Myket), the store, product, a hash of the purchase token and the store's order id. Activation code redemptions and the resulting subscription periods.
- **Abuse prevention:** a record that a device hash has used a free trial, and a SHA-256 hash of each email address that received a free trial.
- **IP address:** used in memory to deliver responses and to rate-limit sign-in, sign-up, verification and payment attempts; it is not stored in the account database.
- **Emails:** verification codes and links, password reset links and one-time website sign-in links are stored only as hashes and expire (after 5 minutes to 48 hours).

The app keeps a copy of the signed license, the session token (in Android Keystore-backed encrypted storage or the desktop operating system's keychain) and the account email on the device. These files are excluded from Android backups.

### Why it is used
To create and secure the account, verify the email address, run the 7-day free trial (one trial per email address and per device) and paid plans, enforce the number of devices per plan, prevent trial abuse, process and verify payments, send transactional emails (verification, password reset, password changed, account deleted), and tell the app when an update is required. The service is not used for advertising, profiling, or selling data.

### Who receives it
- the hosting provider that runs the service;
- the email provider used to send transactional emails (recipient address and message content);
- Zarinpal, for payments made through it (amount, a description, the order id and the account email address);
- Google Play, Cafe Bazaar or Myket, when a purchase is made through that store (the service asks the store to confirm the purchase);
- the host of the darwvin.com website, which forwards account requests from the website to the service.

### What is not sent to Darwvin
Call audio and video, call content, recordings, SIP messages, voicemail and diagnostic traces are never sent to the Darwvin account service. Unless the user turns on sync (below), SIP account credentials, contacts, call history and call notes are not sent either; they stay on the device or go only to the services described in the sections below. The phone's own address book is never uploaded.

### End-to-end encrypted sync between your devices (opt-in)
Sync is off until the user turns it on ("Sync my data between devices") in the Android or desktop app. When it is on, the app synchronises these items between the devices signed in to the same Darwvin account: SIP accounts **including their SIP and TURN passwords**, the Darwvin contacts of the desktop app (Android shows them but does not edit them), call history (the newest 5,000 calls of the last year), call notes, speed dial, and the app language; the desktop app also synchronises its "record every call" setting (the Android app only keeps the value the desktop set and does not change it). Accounts provisioned by an organization (managed accounts), their calls, notes and speed dials are never uploaded. Messages, recordings, voicemail and diagnostics are not synced.

- **End-to-end encryption.** Every item is encrypted on the device with AES-256-GCM under a random data key before it is sent. The data key never leaves the user's devices unencrypted: the service stores it only wrapped (encrypted) with a key derived from the account password (Argon2id) and with a key derived from a **recovery key** that the app shows once when sync is first turned on. Devices keep the data key in the Android Keystore-protected storage or the desktop operating system's keychain. Darwvin, its hosting provider and anyone with a copy of the database or its backups cannot read synced names, numbers, SIP passwords or notes.
- **What the service can see.** For each synced item: the kind of item (for example "contacts" or "calls"), a random item identifier, a revision number, whether it was deleted, the time the app says it was changed, which of the account's devices wrote it, and its encrypted size; for the account: the number and total size of synced items and when the sync key was set up or changed.
- **Recovery key and password reset.** The recovery key is needed if the password is reset (forgot password) and no device that still has the data key is available. Without either, the synchronised copy on the service cannot be decrypted by anyone, including Darwvin; the only option is "Start fresh", which deletes the server copy (each device keeps its local data and can upload it again). Changing the password in the app keeps sync working; after a password change on the website, a device that has the data key asks for the new password once. Until a device has done that, the wrapped data key on the service still opens with the previous password (after a reset, with the forgotten one), so someone who knew the old password and obtained the wrapped key could still decrypt the synced data; opening the app on a device with sync on and entering the new password (or "Start fresh") ends that.
- **Deletion.** Turning sync off on a device removes that device's copy of the data key; the server copy stays for the account's other devices. "Start fresh" deletes all synchronised data and keys on the service. Deleted items are kept only as small encrypted deletion markers (without the item's content) for 180 days so that other devices can remove them too; the markers are sealed with the data key, so the service cannot delete items on the devices by itself. Deleting the Darwvin account deletes all synchronised data and keys.
- **Limitation.** Because the account password is also sent to the service to sign in, a maliciously modified service could capture it at sign-in and use it to unwrap the data key. A separate sync passphrase may be offered later.

### Retention and deletion
Account data is kept while the account exists. Each app sign-in has a record (device identifier hash, device name, platform, app version and times): signing out or removing a device ends the sign-in, and the record is deleted 90 days after the sign-in ended or expired, and at the latest when the account is deleted. App sign-ins expire 60 days after last use and website sign-ins after 12 hours (30 days when "remember me" is chosen); ended website sign-ins are deleted after a week. Users can delete their account in the app (Account > Delete account) or at https://darwvin.com/account/delete. Deletion removes the account (email, name, password hash), all sign-ins, the device list, subscriptions and any remaining paid time, all tokens, and all end-to-end encrypted sync data and keys; a confirmation email is sent. The following are kept after deletion without a link to the account: payment and store purchase records (for accounting and legal obligations), the trial-used records of the account's devices, and the hash of the email address (so that deleting and re-creating an account does not give a new free trial). Data stored only on the device stays there until the app is uninstalled or its data is cleared. Both apps offer "Export my data", also while the app is locked (but not while an app update is required): the Android app creates one JSON file with SIP accounts (without passwords), call history, call notes, speed dial and app settings (Android contacts stay in the phone's own address book and are not part of the export); the desktop app creates one ZIP file with SIP accounts (without passwords), contacts, call history with notes, settings and, if chosen, call recordings. The file is created on the device and shared only where the user chooses.

Signing out or deleting the Darwvin account does not delete data stored on the device. If a different Darwvin account later signs in on the same device, neither app uses or exports the previous account's local data until the user chooses to keep it for the new account or to remove it. On the desktop, removing deletes the SIP accounts with their stored passwords, contacts, call history, messages, recordings and diagnostics; device settings stay. On Android, calling, registration and incoming calls stay off until the choice is made, and removing (after a confirmation) deletes the SIP accounts with their stored passwords, call history, call notes, speed dial, queues, watched lines, message read marks, recordings and the SIP trace; appearance and call settings and an organization's certificate stay.

## Data Darwvin Softphone processes on the device

### SIP and PBX account data
Darwvin Softphone stores SIP server details, usernames, SIP passwords, realms, outbound proxies, TURN credentials, and account preferences in app-private storage. The persisted account data is encrypted with AES-256-GCM using a key held by Android Keystore.

Account data is used to communicate with the SIP/PBX, STUN, and TURN services selected by the user or their provider. SIP credentials are sent to the Darwvin account service only when the user turns on sync, and then only end-to-end encrypted (see "End-to-end encrypted sync between your devices").

### Calls and media
Voice and video media are exchanged with the user's configured SIP/media infrastructure and remote call participants. Darwvin Softphone does not upload call audio or video to a Darwvin-operated server.

Call recordings are optional, require an explicit in-app confirmation before recording begins, and are stored in app-private local storage. Users can select a recording retention policy (30 days, 90 days, 1 year, or Forever), delete recordings manually, or clear app data. Users can explicitly share a recording through Android's system share sheet.

### Call history
Darwvin Softphone keeps a local history of SIP calls made or received through the app. The database is app-private and bounded to the most recent 1,000 entries. Users can clear this history from the app.

### Contacts
If the user grants Contacts permission, Darwvin Softphone reads device contacts locally to help identify and dial contacts. The device address book is never uploaded to a Darwvin-operated service. With sync on, Darwvin's own contacts (created in the desktop app) are synchronised end-to-end encrypted and shown in the Android app.

### Push notifications
When Firebase Cloud Messaging is configured, Google/Firebase provides an FCM registration token. Darwvin Softphone stores that token locally and may include it in RFC 8599 SIP Contact parameters sent to the user's configured SIP registrar so the registrar can request a wake-up for an incoming call. Firebase/Google and the user's SIP provider process data under their own terms and privacy policies.

Firebase push support is optional; direct SIP operation does not require Darwvin to operate a push backend. If Firebase configuration is removed or switched to a different Firebase project, Darwvin Softphone discards the previously stored Firebase project/token pair before later SIP registrations can advertise it.

### QR provisioning and enterprise enrollment
QR provisioning uses Google Code Scanner from Google Play services. Darwvin Softphone parses local/static provisioning data on-device.

For managed enterprise enrollment, a scanned QR code or `darwphone://enroll` deep link may contain an HTTPS enrollment endpoint and a one-time bearer token. Before an external/browsable enrollment link causes a network request, Darwvin Softphone validates the link and asks the user to confirm the destination host. If the user continues, Darwvin Softphone sends the one-time token in the HTTPS `Authorization` header, together with an app-generated installation identifier and a device manufacturer/model label, to the explicitly named enrollment endpoint. The enrollment response can contain SIP/PBX credentials and managed feature policy. Darwvin Softphone validates the response before presenting the account for review and stores accepted credentials only in the encrypted account store. Enrollment redirects are not followed, the endpoint must use HTTPS, and SIP/TURN passwords are not accepted directly in external deep-link URLs.

The enterprise enrollment endpoint is operated by the user's organization/provider or another endpoint represented by the enrollment link; this build does not require a Darwvin-operated enrollment backend.

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

The current Darwvin Softphone codebase does not include an advertising SDK or a Darwvin-operated analytics backend. The Darwvin account service is used only for the account, license, payment, update and opt-in encrypted sync functions described above.

## Data retention

Darwvin account service data: as described in "Retention and deletion" above. End-to-end encrypted sync data: until sync is started fresh or the account is deleted; encrypted markers of deleted items (without their content) for 180 days.

On the device:

- Encrypted SIP account data: until the account is removed or app data is cleared.
- Call history: up to 1,000 local entries, until cleared.
- Call recordings: according to the user-selected retention policy (30 days, 90 days, 1 year, or Forever), unless deleted sooner or app data is cleared.
- FCM token and Firebase project pairing: until replaced by Firebase, Firebase configuration is removed/changed, or app data is cleared.
- Developer SIP trace: bounded local/in-memory diagnostic data while Developer Mode is enabled; exported only by explicit user action.
- SIP instant messages: kept in app-private storage on the device (the most recent 10,000 messages), so conversations survive restarts. They are deleted when the SIP account they belong to is removed, when all accounts are cleared, or when app data is cleared. They are not sent to Darwvin.
- Enterprise enrollment token: held only for the enrollment request and not intentionally persisted as an account credential.
- App-generated enterprise installation identifier: stored in app-private preferences for the app installation and removed when app data is cleared/uninstalled.
- Enterprise device label: derived from the device manufacturer/model for the confirmed enrollment request and not maintained as a separate Darwvin profile by this build.

## Data sharing

Darwvin Softphone shares data only as needed with:
- the Darwvin account service and the recipients listed in "Who receives it" above;
- the SIP/PBX, STUN, and TURN services configured by the user or provider;
- the HTTPS enterprise enrollment endpoint named by an enrollment QR/deep link, after the user confirms that enrollment, when enterprise enrollment is used;
- Firebase Cloud Messaging when push is enabled;
- Google Play services for the code-scanner component;
- destinations explicitly selected by the user through Android sharing.

Darwvin Softphone does not sell user data.

## Security

Persisted SIP credentials use Android Keystore-backed authenticated encryption. Synchronised data is end-to-end encrypted with AES-256-GCM on the device; the service stores only ciphertext and wrapped keys. Communication with the Darwvin account service uses HTTPS; passwords are stored only as bcrypt hashes, session and email tokens only as SHA-256 hashes, and the license is signed with Ed25519 so it cannot be altered on the device. Android app-private storage is used for call history and recordings. TLS/SRTP options are available for compatible SIP providers. Enterprise enrollment requires HTTPS, does not follow redirects, and external/browsable enrollment links require user confirmation before the enrollment request is sent. No security mechanism can guarantee absolute protection.

## Your choices and rights

You can view your account, devices and purchases in the app and at https://darwvin.com/account, change your password, sign devices out, export your data from the app, and delete your account at any time. For any other request about your data, contact us at the address below.

## Children

Darwvin Softphone is not directed to children.

## Changes

Material changes to this policy will update the effective date and should be published before or alongside the corresponding app release.

## Contact

Darwvin Softphone is published by **darwvin-dev / Darwvin**. For privacy or support inquiries, contact **darwvindev@gmail.com**.

Public policy URL: https://darwvin-dev.github.io/screenshot-organizer-legal/darwphone/
