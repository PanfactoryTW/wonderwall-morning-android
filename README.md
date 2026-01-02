# wonderwall-morning-android
A logic-gated Android alarm system that triggers Spotify/YouTube URLs and enforces cognitive wakefulness via system-level overlays and custom passphrases.

# Wonderwall Morning (Android)

> "Because maybe, you're gonna be the one that saves me... from oversleeping."

## 1. Product Purpose
Designed for high-context thinkers and creative professionals, **Wonderwall Morning** bridges the gap between waking up and reaching full cognitive function. By combining "Emotional Stimuli" (via streaming media) with a "Cognitive Load Threshold" (passphrase entry), the app ensures the user enters a logical state of mind immediately, preventing the mindless "snooze-and-drift" cycle.

## 2. Core Logic Flow
The application executes the following system-level orchestration:

1. **Trigger**: Utilizes `AlarmManager` to fire exact alarms, compliant with Android 12+ (API 31+) scheduling requirements.
2. **Audio Enforcement**: Interfaces with `AudioManager` to force-set `STREAM_MUSIC` to a predefined gain (default: 60%) to ensure immediate auditory engagement.
3. **Intent Dispatching**: Dispatches an Implicit Intent to resolve and launch user-defined streaming URLs (e.g., specific Spotify tracks/playlists or YouTube videos).
4. **The "Wonderwall" (Overlay)**: 
   - Invokes a `SYSTEM_ALERT_WINDOW` for a full-screen UI takeover.
   - Intercepts system navigation (Back/Home) to maximize the "cost of bypass."
   - Provides a "Mental Prompt" input field; the alarm is only dismissed upon successful passphrase validation.

## 3. QA & Engineering Requirements (Testing Focus)
As a product developed by a QA/Automation professional, reliability is the primary KPI:
- **Reliability**: Validation of wake-up success rates under **Doze Mode** (Deep Idle) and aggressive OEM power management profiles.
- **Failover Logic**: Implementation of a 10-second watchdog; if the third-party stream fails to output audio, the system triggers a local fallback audio resource.
- **Compatibility**: Verification of Z-index stability and Overlay visibility across both Keyguard (Lock Screen) and Unlocked system states.

## 4. Roadmap
- **Creative Integration**: Support for local high-fidelity audio playback (catered to musicians for demo review).
- **Post-Wake Automation**: Successful validation triggers downstream automation scripts (e.g., TTS summary of the first Google Calendar event or updating Slack status to "Active").
