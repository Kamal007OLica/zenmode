# ZenMode Milestone 02 Product Requirements Document

## Overview

ZenMode is an open-source digital wellbeing launcher that interrupts doom scrolling and helps users build healthier phone habits through resistance screens, accountability buddies, streaks, and mindful interactions.

Milestone 02 focuses on stronger distraction blocking, better engagement loops, social accountability, premium monetization, analytics and habit insights, and UX polish.

## Success Metrics

### Product KPIs

- Increase daily active users by 25%.
- Increase average session completion by 40%.
- Reduce social media opens by 15%.
- Increase 7-day retention by 20%.
- Increase buddy feature adoption to 30%.
- Increase streak participation to 50%.

### Technical KPIs

- Crash-free sessions above 99.5%.
- App startup time under 1.5 seconds.
- Resistance screen launch latency under 300 milliseconds.

## Monetization

### Pro Version

The Pro tier should generate sustainable revenue while keeping core wellbeing features free.

#### Free Tier

- Resistance screen.
- Basic stats.
- Basic streaks.
- Basic buddy.

#### Pro Tier

- Advanced analytics.
- Historical trends.
- Individual app limits.
- Sleep mode.
- Grayscale mode.
- Dynamic Island mindfulness meter.
- Advanced buddy customization.
- Custom interruption screens.
- Premium pets.
- Future AI coaching features.

### Rewarded Ads

Rewarded ads allow users to continue focus sessions after free continuation credits are exhausted.

#### User Flow

1. Show continuation dialog.
2. Let the user watch a rewarded ad.
3. Unlock one continuation.
4. Return to the session.

#### Requirements

- Keep ads non-intrusive.
- Never interrupt an active focus session.
- Respect Google Play rewarded ads policies: <https://support.google.com/googleplay/android-developer/answer/16926792>.

## Core Features

### 1. Social Feed Blocking Improvements

#### Problem

Current blockers can be bypassed or fail in some scenarios.

#### Requirements

Block these surfaces:

- Instagram Reels.
- YouTube Shorts.
- LinkedIn Feed.
- Auto-playing YouTube content.
- Picture-in-picture doom scrolling.

#### Acceptance Criteria

- Feed never loads when blocking is enabled.
- Picture-in-picture closes automatically.
- Blocking survives app relaunch.

### 2. Resistance Screen 2.0

#### Current Issues

- Repetitive feedback.
- Limited emotional engagement.

#### Motion Design

Flow:

1. Resistance Screen.
2. Success Transition.
3. Home Screen Landing.

#### Requirements

- Micro animations.
- Haptic feedback.
- Optional vibration effect.
- Smooth landing transition.

#### New Components

- App usage visualization.
- Daily focus score.
- Buddy encouragement.
- Pet reactions.

### 3. Buddy System Redesign

#### Goal

Create accountability through social motivation.

#### Buddy Connect Flow

Redesign onboarding from code sharing into a visual guided flow with:

- Invite link.
- QR code.
- Telegram community entry.

#### Buddy Home

- Friend greetings.
- Weekly comparison.
- Friendly competition.
- Encouragement messages.

#### Buddy Reactions

- Reaction-only cards.
- Remove unnecessary action state.
- Lightweight notifications.

### 4. Pet Companion System

#### Goal

Create emotional attachment.

#### Evolution Inputs

The pet evolves based on:

- Streaks.
- Reduced screen time.
- Session completion.

#### Pet Reactions

- Happy when a session is completed.
- Sad after excessive scrolling.
- Excited when a new streak is achieved.

#### Future

- Premium pet skins in Pro.

### 5. Stats Experience Redesign

#### Problem

Current stats feel utilitarian.

#### New Information Architecture

##### Daily View

- Screen time.
- Focus time.
- Interruptions.
- Wins.

##### Weekly View

- Trend charts.
- Focus score.
- Improvement percentage.

##### Monthly Wrap

Inspired by Spotify Wrapped, Year in Pixels, and Duolingo Recap.

#### New Metrics

Show comparative habit insights such as:

- `7% better than previous week`.
- `23% fewer social opens`.
- `5-day consistency streak`.

#### Shareable Cards

Generate image exports for:

- Daily wrap.
- Weekly wrap.
- Monthly wrap.

### 6. Streak Redesign

#### Streak Dashboard

Show:

- Current streak.
- Longest streak.
- Weekly consistency.
- Recovery status.

#### Motivational Elements

- Pet integration.
- Buddy reactions.
- Progress celebrations.

### 7. Overlay Doom Scroll Detection

#### Goal

Detect passive scrolling patterns.

#### Triggers

- Long continuous scrolling.
- Repeated app switching.
- Excessive social media opens.

#### Overlay Actions

Show an overlay that asks `Still intentional?` with these options:

- Continue.
- Exit app.
- Start focus session.

### 8. App Management Improvements

#### Hide Apps

Allow users to hide and show apps.

#### Reorder Apps

Allow custom ordering except for protected social apps.

### 9. Landscape Interruption Support

#### Problem

Current call to action is missing in landscape mode.

#### Requirements

Support:

- Portrait.
- Landscape.
- Foldables.

### 10. Emoji Limitation Upgrade

Move from emoji-only feedback to emoji plus optional text. Examples:

- 🙂 `I only need 5 minutes`.
- 😅 `Checking notifications`.

## Nice-to-Have Features

### Sleep Mode

Automatically adapt to night hours and wind-down routines.

### Grayscale Mode

Optionally enable grayscale during focus sessions and sleep mode.

### Dynamic Island Mindfulness Meter for iOS

Display focus progress, session countdown, and daily score.

### Search Motion Design

Improve discoverability and delight.

### App Usage Circle Visualization

Show most opened apps, time spent, and frequency in resistance screens or app launch interruptions.

## Analytics

### PostHog Tracking

Track daily, weekly, and lifetime wellbeing signals.

#### Daily

- Screen time.
- Focus time.
- App opens.

#### Weekly

- Total screen time.
- Streak completion.
- Session success rate.

#### Lifetime

- Total focus hours.
- Time saved.
- Sessions completed.

#### Requirements

- Anonymous IDs.
- Privacy-first tracking.
- GDPR compliance.

## Design and UX Fixes

### High Priority Onboarding Cleanup

#### Issues

- Too much green.
- Excessive contrast.

#### Requirements

- Softer palette.
- Better visual hierarchy.

### Branding

Replace the pixelated logo with a vector asset.

### Attribution Tracking

Add onboarding source tracking with options such as:

- Reddit.
- Product Hunt.
- Telegram.
- YouTube.
- Organic.

### Release Notes System

Support Evernote- and Spotify-inspired release notes with:

- Banner cards.
- Feature announcements.
- Changelog entries.

## Technical Requirements

### Android Device Admin Permissions

Review whether Device Admin permissions are still necessary and investigate alternatives such as Accessibility Service and Usage Access APIs.

### Picture-in-Picture Handling

Detect YouTube and media apps, then trigger interruption logic when picture-in-picture doom scrolling is detected.

### Telegram Community

Add `Join ZenMode Community` entry points in Settings and Buddy onboarding.

## Bugs

### Critical Escape Loophole

#### Issue

Users can bypass the 7-second timer by tapping outside the dialog.

#### Fix

- Prevent dismissal.
- Maintain countdown state.

### Remember and Do Not Disturb

Investigate persistence failures.

### Repetitive Resistance Feedback

Add feedback rotation, randomized content, and context-aware prompts.

## Compliance

Before release, review App Store and Play Store requirements for:

- Rewarded ads policy.
- Accessibility permissions.
- Device admin permissions.

## Open Source and Distribution

### F-Droid

- Follow up on publication.
- Update metadata.
- Add release automation.

### Funding Opportunities

Research FLOSS Fund and KDE Sponsorship.

## Future Exploration

### iOS

Investigate PWA support, Tauri packaging, and native alternatives.

### Website

Create a modern landing page inspired by PostHog with these pages:

- Home.
- Features.
- Roadmap.
- Changelog.
- Privacy.
- Open Source.

## Deliverables

### Design

- Buddy redesign.
- Streak redesign.
- Stats redesign.
- Pet system.
- Resistance motion design.
- Updated onboarding.

### Engineering

- Feed blocking improvements.
- Picture-in-picture detection.
- Analytics.
- Pro subscription.
- Rewarded ads.
- Shareable wraps.

### Content

- Privacy policy update.
- Onboarding guide.
- YouTube tutorial.
- Release notes system.

## Priority Breakdown

### P0: Must Ship

- Feed blocking improvements.
- Picture-in-picture handling.
- Resistance redesign.
- Buddy redesign.
- Stats redesign.
- Escape loophole fix.
- Onboarding cleanup.

### P1: Should Ship

- Pet system.
- Shareable wraps.
- Telegram integration.
- Rewarded ads.
- Release notes.

### P2: Nice To Have

- Sleep mode.
- Grayscale mode.
- Dynamic Island.
- App ordering.
- Search animations.

## Release Target

ZenMode Milestone 02.
