# Sakay Na!

A one-tap Filipino road game. Drive a jeepney, tricycle, taxi, UV Express or provincial bus from Metro Manila to Ilocos and Bicol, pick up passengers, dodge traffic, and grab power-ups.

**Play:** https://shishieyo.github.io/sakay-na/

## Controls
- Tap the left or right side of the screen to switch lanes
- Keyboard: ← → or A / D

## What's in it
- 12 routes in three regions: Metro Manila (EDSA, NLEX, SLEX, Roxas Blvd), Biyaheng Norte (SCTEX, TPLEX, La Union, Ilocos) and Biyaheng Bicol (Quezon, Bitukang Manok, Camarines Sur, Albay)
- Up to 3 stars per route, based on passengers picked up
- Endless ride mode
- Power-ups: Turbo, Magnet, Anting-anting, Rush Hour 2×
- Missions, a garage of vehicles, jeepney paint jobs and taxi paints (white or yellow), and Kita (in-game earnings)

## Prototype notes
- Top-up purchases are placeholders. No real money is charged. Rewarded ads are a countdown placeholder on the web and real AdMob ads (Google test ads for now) in the Android app.
- Progress resets when the page is reloaded on this site. Saving and the Top drivers leaderboard only work in the Claude-hosted version.
- Planned for the store release: Phaser build, Google Play / App Store billing, Google Play Games and Game Center leaderboards.

## Android app (Capacitor + AdMob)
```
npm install
npm run sync        # copies index.html + capacitor.js to www/ and syncs the Android project
npx cap open android
```
Requires Android Studio. The app uses Google's AdMob test IDs; replace them before release (see `docs/superpowers/specs/2026-10-12-admob-rewarded-ads-design.md`).
