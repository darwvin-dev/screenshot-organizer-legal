---
title: Screenshot Organizer — Privacy Policy
description: Privacy policy for the Screenshot Organizer Android app.
---

# Screenshot Organizer Privacy Policy

_Last updated: September 1, 2026_

Screenshot Organizer is designed as a local-first Android application for finding, organizing, annotating, and revisiting screenshots stored on a user's device.

## Data the app accesses

When the user explicitly enables screenshot monitoring, Screenshot Organizer may request access to images available through Android MediaStore. Broad image access is used because the core organizer experience needs to discover screenshots created across the device; a one-time picker cannot provide continuous screenshot discovery.

The app may process the following information locally on the device:

- screenshot image content needed for local image hashing and on-device OCR;
- screenshot filename, dimensions, capture time, MediaStore URI, and available source-app metadata;
- OCR text derived from screenshots;
- folders, notes, tags, reminders, favorites, organization history, attachment references, automation rules, and custom folder templates created by the user;
- local similarity features used to suggest or automatically organize screenshots when Smart Organizer is enabled;
- local operational diagnostics such as last reconciliation time and accepted/rejected screenshot counts.

## How data is used

The data above is used only to provide user-facing organizer functionality, including screenshot discovery, local search, folders, notes, tags, reminders, attachments, automation rules, smart suggestions, reversible automatic organization, and local recovery after process death or device restart.

## Local processing and network access

The Android application does not request the `INTERNET` permission. Screenshot OCR and similarity processing are performed on-device. The app does not upload screenshot content, OCR text, notes, tags, or organizer metadata to a Screenshot Organizer server.

## Advertising, analytics, and accounts

The current application does not include an advertising SDK, analytics SDK, cloud account system, or cloud screenshot-processing service.

## Original screenshot files

Screenshot Organizer references original images stored in Android MediaStore. Clearing organizer metadata does not delete original screenshot files. If an original image is deleted outside the app, Screenshot Organizer records the source as missing during reconciliation.

## Notifications and foreground monitoring

If enabled by the user, the app may show notifications for newly detected screenshots and reminders. Reliable realtime monitoring may use a visible Android foreground-service notification. Monitoring can be disabled from the app, and the service is not intended to run without the user's persisted choice and required Android permissions.

## Optional App Lock

Screenshot Organizer can optionally protect the organizer interface using Android's system biometric/device-credential prompt. Authentication is performed by Android; Screenshot Organizer receives only the success, failure, or cancellation result and does not receive or store fingerprint, face, PIN, pattern, or password data.

When App Lock is enabled, the app also marks its Activity as secure so protected organizer content is not intentionally exposed through ordinary screenshots or recent-app previews. App Lock protects access to the app interface; it does not encrypt original screenshots stored by Android MediaStore.

## Backups

Portable organizer backups never copy screenshot image bytes. A backup can contain folders, screenshot metadata, notes, tags, reminders, favorites, organization history, attachment references, automation rules/templates, OCR text, and local derived smart metadata.

Backup encryption is user controlled:

- If the user supplies a passphrase of at least 8 characters, the app encrypts the backup on-device using a password-derived key and authenticated AES-256-GCM encryption.
- If the user intentionally leaves the passphrase blank, the app creates an unencrypted JSON backup. Anyone who obtains that file may be able to read the organizer metadata it contains.
- A non-empty passphrase shorter than 8 characters is rejected rather than silently falling back to plaintext.

The app clearly identifies the selected backup mode before export. Users who choose an unencrypted backup should protect the exported file using the storage/location controls of the destination they select. Screenshot attachment files themselves are not copied into the backup; only their stored document references and metadata are included, and those references may not remain accessible on another device or installation.

Android platform backup of app-owned organizer data is disabled by the application configuration.

## Data sharing and sale

Screenshot Organizer does not sell personal data. The current application does not transmit organizer data to advertising networks, analytics providers, or a Screenshot Organizer backend.

When a user explicitly exports a backup or invokes Android sharing/opening flows, the destination chosen by the user is outside Screenshot Organizer's control and is governed by that destination's privacy practices. This applies to both encrypted and intentionally unencrypted backup exports.

## Data retention and deletion

Organizer metadata remains on the device until the user removes it, clears application data, uninstalls the app, or imports a replacement organizer backup. The app provides controls to clear derived smart data separately from core organizer metadata.

Original screenshots remain governed by Android MediaStore and the user's gallery/file-management actions.

## Permissions

Depending on Android version and enabled features, the app may request:

- image/media read access for screenshot discovery;
- selected-photo access state on supported Android versions;
- notification permission for screenshot and reminder notifications;
- foreground-service permission for user-enabled realtime monitoring;
- boot-completed reception to reconcile persisted monitoring state after restart;
- biometric/device-credential authentication for optional App Lock.

Permissions are used only for the corresponding user-facing features and can be revoked through Android system settings.

## Children's privacy

Screenshot Organizer is a general productivity utility and is not designed specifically for children. The application does not knowingly operate a cloud service that collects children's screenshot data.

## Changes to this policy

If application behavior changes in a way that affects data access, collection, processing, sharing, or retention, this policy must be updated before the corresponding release is distributed.

## Contact

For questions about this policy or about privacy in Screenshot Organizer, contact:

**darwvindev@gmail.com**
