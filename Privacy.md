# LumeAir Home Privacy Policy

**Effective October 28, 2026**

## At a glance

LumeAir Home doesn't collect your personal information: there are no accounts, no analytics, no ads, and no LumeAir servers. Everything the app knows stays on your phone and on your own LumeAir sensors, on your home network.

- Your air-quality readings travel only between your sensors and your phone, over your Wi-Fi.
- Your Wi-Fi password goes from your phone to your sensor over Bluetooth during setup, encrypted so nearby devices can't read it. The app doesn't keep it.
- If you turn on phone notifications, your sensors send alerts through ntfy or Pushover, services you choose and set up yourself.
- To check for firmware updates, the app reads a small file from our release page on GitHub, and your sensor downloads an update from there when you tap **Update**. Like any website, GitHub sees your IP address; no readings or settings are sent.
- We never sell, share or rent your information.

## Who we are and what this covers

This policy covers the LumeAir Home app for Android and iOS and the firmware that runs on LumeAir sensors. LumeAir Home is made by Kyle Bourgoin ("LumeAir", "we").

It doesn't cover third-party services you choose to use with the app, such as ntfy, Pushover, Google Play or Apple's App Store. Their own privacy policies apply to them.

## What the app stores on your phone

The app keeps only what it needs to show your sensors and their alerts. None of it leaves your phone, except as described in [Third-party services](#third-party-services) below.

| Information | Why | Where it's kept |
|---|---|---|
| Each sensor's network address, the room name you give it, and its firmware version | To find and show your sensors | App storage on your phone |
| Each sensor's access key | So only your app can read your sensors | Encrypted storage (Android Keystore or iOS Keychain) |
| Recent readings, up to 7 days | Charts and trends, even while a sensor is offline | A database on your phone |
| Your settings: units, alert thresholds, quiet hours, theme | To remember your choices | App storage on your phone |
| ntfy or Pushover details, if you set them up | To configure your sensors' notifications | Encrypted storage |
| Which alerts you've already seen | So the app only shows new ones | App storage on your phone |

The app doesn't store your Wi-Fi password. During setup it encrypts it and passes it straight to your sensor over Bluetooth.

If you share a sensor with another phone using a pair code, the code contains that sensor's network address and access key. Anyone with the code can read that sensor's readings while on your network, so share it only with people you trust.

## What your sensors store

Each LumeAir sensor keeps its own settings and readings in its built-in memory. Nothing on a sensor is sent to us.

- Your Wi-Fi network name and password, so it can reconnect.
- Its access key, which it requires on every request from the app.
- Its readings for the last 7 days and a log of its last 64 alerts.
- Your alert thresholds, quiet hours and time zone.
- The room name and ntfy or Pushover details, if you set up notifications.

On your home network, the app and sensor talk over plain HTTP, and every request must carry the sensor's access key. The sensor accepts Bluetooth setup connections only when it has no Wi-Fi settings, and for 2 minutes after it restarts. Once set up, it accepts new Wi-Fi details only from a phone that holds its access key.

## Permissions and why we ask

The app asks only for permissions it uses, and only when it needs them.

| Permission | When | Why |
|---|---|---|
| Bluetooth (Nearby devices) | Setting up a new sensor | To find the sensor and give it your Wi-Fi details. We tell Android we don't use it to work out your location. |
| Location (Android 11 and older only) | Setting up a new sensor | Older Android versions require it for any Bluetooth scan. The app never reads your location. |
| Camera | Scanning a pair code | To read the QR code. The image is processed on your phone and never saved or sent. |
| Local network and Wi-Fi | While the app is open | To find your sensors and read them over your home network. |
| Internet | While the app is open | To reach your sensors, to check for firmware updates, and to check Pushover codes if you set up Pushover. |

The app doesn't ask to send you notifications itself. Alerts come from your sensors through the notification app you choose.

## Third-party services

Apart from the firmware update check, these services are involved only when you choose to use them. We don't control them, and their own privacy policies apply.

| Service | When it's used | What it receives |
|---|---|---|
| GitHub Pages | The app checks for a firmware update when you open Settings, at most every 6 hours. A sensor downloads an update only when you tap **Update**. | Your IP address and the time of each request, as for any website. The requests carry no readings, settings, access keys or account details. GitHub hosts our release files; we don't receive its visitor logs. |
| ntfy | You turn on notifications through ntfy | Each alert your sensors send: its title, the room name, the reading and your threshold, and a link that opens the app. Alerts go to a topic name the app generates at random, sent to ntfy.sh unless you enter your own ntfy server. |
| Pushover | You turn on notifications through Pushover | The same alert details, plus your Pushover app token and user key. During setup, the app also sends those two codes to Pushover once to check them. |
| Google Play or Apple's App Store | You install or update the app | What their own policies describe, such as crash reports if you've allowed your phone to share them with developers. |

Anyone who knows your ntfy topic name can read alerts sent to it on a public server. The app makes it long and random so it can't be guessed. Treat it like a password, or use your own ntfy server.

## What we don't do

- No accounts, sign-in, or email address required.
- No analytics, advertising, or tracking SDKs, and no advertising ID.
- No LumeAir servers: we never receive your readings, settings or location.
- No selling, renting or sharing of your information with anyone.

## Keeping and deleting your information

You control all of it, because it lives on your own devices.

- **On your phone:** readings older than 7 days are deleted automatically. Removing a sensor in the app deletes its details and readings. Uninstalling the app deletes everything it stored.
- **Backups:** Android may include the app's settings in your phone's backup to your Google account, as it does for most apps. Access keys are encrypted with a key that never leaves your phone, so a restored backup can't read them.
- **On your sensors:** readings older than 7 days and alerts beyond the last 64 are dropped automatically. Turning off phone notifications in the app erases the ntfy or Pushover details from your sensors. To erase a sensor completely, factory reset it from the app (**Settings › Sensors**), or hold its BOOT button for 10 seconds.
- **With third parties:** alerts already sent to ntfy or Pushover are kept as their policies describe.

## Security

Each sensor gets its own random access key during setup, and it answers only requests that carry it. The app keeps those keys, and your ntfy or Pushover details, in your phone's encrypted storage. Sensors send notifications to ntfy and Pushover over HTTPS. Firmware updates are downloaded over HTTPS and signed: a sensor installs one only if its signature matches LumeAir's key, and otherwise keeps its current firmware.

Inside your home network, the app and sensors talk over plain HTTP, so your network's Wi-Fi password is what keeps others off it. No system is perfectly secure; if you find a security problem, please tell us using the contact below.

## Children

LumeAir Home is meant for households setting up their own air-quality sensors, not for children. Because the app collects no personal information from anyone, it collects none from children either.

## Changes to this policy

If the app starts handling information differently, we'll update this policy and its effective date before that version of the app is released. Significant changes will also be noted in the app's release notes.

## Contact

Questions about this policy or your information: email us at [lumeair.home@gmail.com](mailto:lumeair.home@gmail.com). We'll reply within 30 days.
