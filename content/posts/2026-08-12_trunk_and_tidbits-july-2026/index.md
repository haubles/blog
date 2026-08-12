---
title: "Trunk & Tidbits, July 2026"
description: "The latest updates on engineering work from the Mastodon team"
date: 2026-08-12
section: Trunk and Tidbits
categories:
  - Trunk and Tidbits
  - Engineering
tags:
  - engineering
  - mastodon
authors:
  - mastodon
resources:
  - name: hero
    src: hero.png
---

Welcome to the 28th edition of Trunks & Tidbits!

This is the summer here in Europe, but while some of the team is enjoying some well-earned vacations, the work on Mastodon continues and we made a lot of progress this month.

The team is continuing to grow, and we are very pleased to welcome [Juan](https://hachyderm.io/@jhbabon) as the 4th member of our web backend team. As we have doubled the size of the backend team over the last few months, we are now all set up to start working on the various projects funded by the Sovereign Tech Agency that [we announced a few months ago](/2026/04/sovereign-tech-agency-funding/).

We also published the [results of our first Discovery Week](/2026/08/discovery-week-2026-what-we-learned-and-what-were-doing-next/). Find out what we learned and what will be our next focuses after this week of user surveys and workshops organised by Imani, our Head of Design.

## Releases

We recently released Mastodon [4.6.3](https://github.com/mastodon/mastodon/releases/tag/v4.6.3), [4.6.4](https://github.com/mastodon/mastodon/releases/tag/v4.6.4) and [4.6.5](https://github.com/mastodon/mastodon/releases/tag/v4.6.5), fixing various bugs and security issues (including one high severity). We recommend all administrators running Mastodon 4.6 to update as soon as possible.

We also backported those fixes for our currently supported versions. If you are not (yet) running Mastodon 4.6, we recommend you to update to either Mastodon [4.5.15](https://github.com/mastodon/mastodon/releases/tag/v4.5.15) or [4.4.22](https://github.com/mastodon/mastodon/releases/tag/v4.4.22).

Finally, we just released the [first beta version for Mastodon 4.7](https://github.com/mastodon/mastodon/releases/tag/v4.7.0-beta.1). It contains very few user-facing changes, but does contain significant reworking of the backend code to improve security and support new protocol features. This requires substantial database migrations that could take a couple of hours on very large servers, but will not cause downtime if the upgrade instructions are followed.

## Backend & Web

In July 2026 we reviewed and merged 204 Pull Requests (120 with translation and dependency updates removed) from 14 contributors.

- Migrated local private keys to a new, on-disk encrypted, database table {{< github-pr id=39686 authors="ClearlyClaire" >}}
- Added support for storing (not yet using) ML-DSA-44 (post-quantum algorithm) account keys {{< github-pr id=39747 authors="ClearlyClaire" >}}
- Added support for `ML-DSA-44` in Object Integrity Proofs (for servers running a recent OpenSSL version) {{< github-pr id=39522 authors="ClearlyClaire" >}}
- Added support for FEP-8b32 {{< github-pr id=39530 authors="ClearlyClaire" >}}
- Added support for sending RFC 9421 HTTP Message signatures. Mastodon will still first send the legacy `cavage-12` signatures for now, due to issues in other Fediverse software {{< github-pr id=39756 authors="ClearlyClaire" >}}
- Added support for `Link` objects in `attachment`  as per [FEP 8967](https://w3id.org/fep/8967) {{< github-pr id=36104 authors="Gargron" >}}
- Two big database changes have been merged to better differentiate between deleted and suspended accounts, and to ensure that an account’s `uri` is unique {{< github-pr id=23617 authors="ClearlyClaire" >}} {{< github-pr id=39882 authors="ClearlyClaire" >}}
- Started to refactor the `<Status>` component to make future changes easier
- Added end-of-life date on the “Available Updates” page and notify admins when they run an out-of-support Mastodon version {{< github-pr id=39732 authors="ClearlyClaire" >}}
- Fixed an issue for the controller handling the web push notification `Unsubscribe-URL` endpoint. This is now working correctly, and we advise client developers that process web push notifications asynchronously to support it to reduce the number of failed requests. Our own push relays [have been](https://github.com/mastodon/webpush-apn-relay/pull/8) [updated](https://github.com/mastodon/webpush-fcm-relay/pull/10) {{< github-pr id=39918 authors="ClearlyClaire" >}}
- Improved Emoji search after the recent refactor {{< github-pr id=39815 authors="chaosexanima" >}}
- Various front-end components have been updated or created in preparation of future interface changes. More new about this very soon!
- Work is in progress to get [Fediscoverer](https://github.com/mastodon/fediscoverer), our provider software for [Fediscovery](https://www.fediscovery.org/), ready to be deployed at scale. Multiple bugs have also been fixed and we are planning to start testing it on heavy traffic servers soon, before making it available for everyone.

## Android & iOS

On Android, version [2.13.2](https://github.com/mastodon/mastodon-android/releases/tag/v2.13.2) has been released to fix a few bugs  and brings the app in compliance with the Google Play target SDK requirement.

For the iOS app, while a large rework of the app is in progress, we released [2026.05](https://github.com/mastodon/mastodon-ios/releases/tag/2026.05) fixing a couple of important bugs with profiles.

## Thanks

Thanks for reading! If you’re excited about what we’re working on, would you consider supporting us with a small, recurring donation?

{{< donate >}}
