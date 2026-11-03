# Privacy policy

**First Seats** (`com.firstseats.app`)

Effective 3 November 2026.

This policy describes how First Seats accesses, collects, uses, stores, and shares information. The operator of the app and this policy is **Jonathan Holderness** (“we”, “us”).

First Seats watches a UK→Europe route on Ryanair, Wizz Air, or easyJet for a date you choose. Once a day it checks public airline calendars and, if you allowed notifications, it can send a push when that date appears on sale.

First Seats does not create user accounts, take payment, or book flights. It is not affiliated with Ryanair DAC, Wizz Air Hungary Ltd., easyJet Airline Company Limited, or any other airline.

## Information we collect

We do not ask for your name, email address, phone number, or payment details.

### On your device

- **Install id.** A random string created on first launch and stored in app storage. It is not your Android advertising id, IMEI, or other hardware identifier. We use it only to load and save this install’s watch list.
- **Onboarding flag.** A local flag so the explainer is not shown every launch.
- **Notification permission.** Android may show a system prompt. If you refuse, watches still save; we cannot send a remote notification.

### When you create a watch (sent to our servers)

We store the following in Amazon DynamoDB in **AWS region eu-west-2 (London)**:

- the install id
- airline code (Ryanair, Wizz Air, or easyJet)
- origin and destination airport codes
- the travel date you asked us to watch
- whether that date is still being watched or already marked on sale
- timestamps (`createdAt`, `lastCheckedAt`)
- an **Expo push token**, if notification permission was granted and token registration succeeded. If not, this field is empty and we do not send a push for that watch.

### Technical data

Your phone talks to our API over **HTTPS**. Amazon Web Services may process standard request metadata (for example IP address, time, and path) in API Gateway, Lambda, CloudWatch Logs, and AWS X-Ray. We use that to run and debug the service, not to build a marketing profile.

We do not use advertising SDKs and we do not sell data.

## How we use information

- Show and update your watch list on this install.
- Check, once a day, whether a watched date appears on sale on public airline calendars.
- Send a push notification to this device when a watched date is marked on sale (only if we have a push token).
- Operate, secure, and fix the app and API.

## Who we share information with

We share data only as needed to run First Seats:

| Recipient | Why |
| --- | --- |
| **Amazon Web Services** (eu-west-2) | API, database, logs, and the daily check. |
| **Expo** (push API) | Deliver the “on sale” notification. The payload includes the route, date, airline, and watch id. Expo then delivers via **Firebase Cloud Messaging** (Google) on Android. |
| **Airlines (from this device)** | To draw the in-app calendar, the phone may call Ryanair or Wizz Air public timetable APIs if our API is unavailable. For easyJet priced days, the app loads `https://www.easyjet.com/en/` in a hidden WebView and reads that route’s availability. Those companies then process whatever their own sites collect (which may include your IP address and cookies) under **their** privacy policies, not this one. |
| **Airlines (from our servers)** | Our daily job and API also request public fare calendars and route lists from Ryanair, Wizz Air, and easyJet. Those requests come from AWS, not from your phone. They contain the route and date being checked, not your install id or push token. |

We do not sell personal information. We may disclose data if required by law.

## Retention and deletion

There is **no account**. Identity is the install id on the device.

- **Delete one watch:** long-press the watch in the app. That row is removed from our database, including its push token.
- **Uninstall or clear app storage:** the local install id is lost. The app can no longer show or delete those watches. Rows may remain on the server until they are removed another way. They are not used to notify a new install.
- We do not currently offer a website form to wipe every watch for an install. To request deletion of remaining server rows, use the contact link below and include the install id if you still have it.

## Security

Watch data is sent over HTTPS. The database is in AWS eu-west-2 with point-in-time recovery. No system is perfectly secure.

## Children

First Seats is not directed at children under 13 (or the equivalent age in your country). We do not knowingly collect personal information from children.

## Your rights

If UK GDPR or similar law applies, you may have rights to access, correct, or delete personal data we hold, and to object to or restrict certain processing. Contact us using the link below. You may also complain to the ICO (UK) or your local supervisory authority.

The lawful bases we rely on are **performance of the service you request** (storing watches and sending the notification you asked for) and **legitimate interests** in running a reliable API (security and logs).

## Changes

If we change this policy, we will update this page and the effective date. Material changes will be described here.

## Contact

Report privacy questions or deletion requests at:

[github.com/jonathanholderness/first_seats_app/issues](https://github.com/jonathanholderness/first_seats_app/issues)

Name the app **First Seats** in the issue.
