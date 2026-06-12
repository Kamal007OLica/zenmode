# Milestone 02 Implementation Plan

This plan converts the Milestone 02 PRD into an execution-oriented roadmap for contributors. It is intentionally organized by dependency order so that design, Android implementation, analytics, and compliance work can move in parallel without blocking the open-source build.

## Guiding Principles

- Keep the free tier useful for core digital wellbeing workflows.
- Preserve privacy-first defaults with anonymous analytics identifiers.
- Keep proprietary integrations behind `core-api` contracts and provide `core-mock` implementations for contributors.
- Ship behavior changes behind small, testable units with clear acceptance criteria.
- Avoid blocking active focus sessions with monetization or promotional prompts.

## Phase 0: Discovery and Risk Reduction

| Workstream | Scope | Output |
| --- | --- | --- |
| Blocking audit | Validate Instagram Reels, YouTube Shorts, LinkedIn Feed, autoplay, and PiP bypass paths. | Repro matrix with package names, UI signatures, and failure modes. |
| Permissions review | Re-evaluate Device Admin, Accessibility Service, Usage Access, overlay, and notification permissions. | Permission decision record with Play Store compliance notes. |
| Analytics taxonomy | Define PostHog event names, properties, and retention windows. | Privacy-reviewed analytics schema. |
| Design foundations | Define softer onboarding palette, vector logo, and motion guidelines. | Shared design tokens and animation specs. |

## Phase 1: P0 Stabilization

### Feed Blocking and PiP Handling

- Expand blocking signatures for Instagram Reels, YouTube Shorts, LinkedIn Feed, and auto-playing YouTube surfaces.
- Add PiP detection for YouTube and supported media apps.
- Persist blocking state across app relaunch and process death.
- Add regression tests around protected package matching and bypass handling.

### Escape Loophole Fix

- Make the 7-second resistance timer non-dismissible until the countdown completes.
- Preserve countdown state across configuration changes.
- Verify that outside taps, back presses, and activity relaunches cannot skip the timer.

### Resistance Screen 2.0

- Introduce rotating and context-aware resistance prompts.
- Add haptic and optional vibration hooks.
- Add usage visualization, daily focus score, buddy encouragement, and pet reaction slots.
- Ensure launch latency stays under 300 milliseconds.

### Buddy Redesign

- Replace code-only sharing with guided invite link, QR code, and Telegram entry points.
- Add Buddy Home modules for greetings, weekly comparison, friendly competition, and encouragement.
- Simplify buddy reactions into reaction-only cards with lightweight notifications.

### Stats Redesign

- Split stats into daily, weekly, and monthly-wrap sections.
- Add comparison metrics such as weekly improvement, fewer social opens, and consistency streaks.
- Define the data model needed for shareable daily, weekly, and monthly cards.

### Onboarding Cleanup

- Apply softer palette and clearer hierarchy.
- Add source attribution options: Reddit, Product Hunt, Telegram, YouTube, and Organic.
- Replace pixelated logo usage with vector artwork.

## Phase 2: P1 Engagement and Monetization

### Pet Companion System

- Add pet state derived from streaks, reduced screen time, and session completion.
- Add happy, sad, and excited reactions.
- Reserve premium skin extension points for Pro.

### Shareable Wraps

- Render daily, weekly, and monthly wrap cards.
- Export wrap cards as images.
- Keep shared images free of private identifiers unless the user explicitly opts in.

### Telegram Integration

- Add `Join ZenMode Community` links in Settings and Buddy onboarding.
- Track entry-point taps anonymously.

### Rewarded Ads

- Add continuation credits and rewarded-ad unlock flow.
- Never display rewarded ads during active focus sessions.
- Add policy review checklist before release.

### Release Notes

- Add banner cards, feature announcements, and changelog support.
- Support local fallback content for offline or mock builds.

## Phase 3: P2 Enhancements

- Sleep mode with night hours and wind-down routine support.
- Grayscale mode during focus sessions and sleep mode.
- Dynamic Island mindfulness meter exploration for iOS.
- Custom app ordering while preserving protected social app behavior.
- Search motion design and app usage circle visualization.

## Analytics Events Draft

| Event | When | Important Properties |
| --- | --- | --- |
| `resistance_screen_shown` | Interruption screen appears. | app_package, trigger, latency_ms, session_id |
| `resistance_screen_completed` | User completes the countdown. | app_package, duration_ms, selected_reason |
| `doom_scroll_overlay_shown` | Passive scrolling overlay appears. | trigger_type, app_package, scroll_duration_ms |
| `buddy_invite_started` | User begins buddy invite flow. | entry_point, invite_type |
| `buddy_reaction_sent` | User sends a reaction-only card. | reaction_type, relationship_age_days |
| `streak_updated` | Streak changes. | current_streak, longest_streak, recovery_status |
| `stats_wrap_exported` | User exports a wrap image. | period, share_target_available |
| `rewarded_ad_continuation_unlocked` | Rewarded ad grants continuation. | credits_remaining, ad_provider |
| `onboarding_source_selected` | User selects attribution source. | source |

## Acceptance Checklist

### P0 Release Gate

- [ ] Feed blocking cannot be bypassed in target surfaces.
- [ ] PiP doom scrolling triggers interruption logic.
- [ ] Blocking state survives app relaunch.
- [ ] Resistance timer cannot be dismissed by outside taps or back navigation.
- [ ] Resistance screen launch latency is under 300 milliseconds on representative devices.
- [ ] Buddy onboarding supports invite link, QR code, and Telegram entry points.
- [ ] Daily and weekly stats views show comparative insights.
- [ ] Onboarding palette, hierarchy, attribution tracking, and vector logo updates are complete.

### P1 Release Gate

- [ ] Pet reactions respond to completed sessions, excessive scrolling, and new streaks.
- [ ] Shareable wrap cards export as images.
- [ ] Telegram community links exist in Settings and Buddy onboarding.
- [ ] Rewarded ads only appear after free continuation credits are exhausted.
- [ ] Release notes can display banner cards and changelog entries.

### Compliance Gate

- [ ] Rewarded ads comply with Google Play policy.
- [ ] Accessibility usage is disclosed and limited to wellbeing functionality.
- [ ] Device Admin requirement is justified or removed.
- [ ] Analytics uses anonymous identifiers and supports GDPR-oriented privacy requirements.
- [ ] Store listings and privacy policy are updated before release.
