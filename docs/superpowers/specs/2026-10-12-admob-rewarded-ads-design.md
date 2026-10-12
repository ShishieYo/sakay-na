# AdMob rewarded ads (Android) – design

## Goal
Replace the placeholder rewarded ad with real AdMob rewarded video in an Android app, without changing the web version on GitHub Pages.

## Decisions
- Wrap the existing `index.html` in Capacitor (no Phaser port, no bundler). Android only; iOS later.
- Rewarded ads only. `runAd(onReward)` keeps its signature, so its three callers (Headstart, +₱ Kita, 2× Kita) are unchanged.
- Native: initialize AdMob, prepare, then show a rewarded ad. `showRewardVideoAd()` resolves only when the reward is earned, and `onReward` runs only then.
- Web: unchanged 5-second countdown placeholder.
- Fail fast: if the ad fails, log the error and tell the user. No reward and no fallback to the fake countdown.
- Google's test ad unit and app IDs are used until an AdMob account exists. Ad unit id: `ADMOB` in `index.html`. App id: `AndroidManifest.xml`.

## Structure
- `index.html` stays at the repo root. `npm run sync` copies it and Capacitor core's `capacitor.js` into `www/` (gitignored) and runs `cap sync android`.
- The Android native bridge injects only `window.Capacitor`, not `registerPlugin`. In the native app, `capacitor.js` is loaded on first ad and `registerPlugin("AdMob")` exposes the plugin. The web build never loads it.

## Before release
Create an AdMob account and app, then replace the test rewarded ad unit id (`index.html`) and the test app id (`AndroidManifest.xml`). Add the UMP consent flow if serving ads in the EEA/UK.
