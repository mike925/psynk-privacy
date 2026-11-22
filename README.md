# Psynk

Psynk is a native iOS and iPadOS bullet journal from Psythletix. The app is SwiftUI, journal entries are stored on device with SwiftData, and a WidgetKit extension reads a small snapshot from a shared App Group.

## Requirements

- Xcode 16 or newer
- iOS / iPadOS 17 or newer

## Run

Open `Psynk.xcodeproj`, select the **Psynk** scheme, and run. The widget extension is embedded in the app target.

The project already sets signing team `7LLJ9PTWBT`. Before the first install on a device, or before an App Store archive, register these identifiers for that team in the Apple Developer portal:

| | Identifier |
|---|---|
| App | `com.psythletix.psynk` |
| Widget extension | `com.psythletix.psynk.widget` |
| App Group | `group.com.psythletix.psynk` |

The app and the widget both use that App Group. They must stay in sync.

A new bundle ID installs as a new app. Journal data already on a test device under an older bundle ID stays with that older install.

## Trial and unlock

Writing is free for 7 days from the first App Store download, then read-only until a one-time unlock (`com.psythletix.psynk.lifetime`). The Psynk scheme’s Run options use `Psynk.storekit` so you can buy and refund that product in Xcode before it exists in App Store Connect. Debug builds add Settings → Profile → Trial clock.

## Layout

- `Psynk/` — app source, asset catalog, fonts, entitlements, and privacy manifest
- `PsynkWidget/` — widget extension
- `Psynk-Splash/` — source artwork for the icon and splash. The running splash is drawn in `SplashView` from the asset catalog.

Settings includes a paper theme named Wooden (`id: wooden`). That is a look, not the product name, and the stored id is unchanged so a saved theme choice still applies.
