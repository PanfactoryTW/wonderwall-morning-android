# Wonderwall Morning (Android)

> "Because maybe, you're gonna be the one that saves me... from oversleeping."

## 1. Summary
**Wonderwall Morning** is a "logic-gated" alarm system designed for high-context thinkers and creative professionals. By integrating **emotional stimuli** via streaming media (Spotify/YouTube) with a **cognitive load threshold** (passphrase entry), the system ensures that users transition into a logical state of mind immediately upon waking, effectively breaking the unconscious "snooze-and-drift" cycle.

## 2. Key Features
* **Intent-Based Media Integration**: Orchestrates implicit intents to launch specific Spotify or YouTube URLs, transforming personalized music or motivational content into wake-up triggers.
* **The "Wonderwall" Overlay**: Implements a system-level `SYSTEM_ALERT_WINDOW` that enforces a full-screen takeover when the alarm triggers, intercepting system navigation (Back/Home) to maximize the cost of bypass.
* **Cognitive Gate (Passphrase)**: Users must accurately input a predefined "mental prompt" to release the lock and terminate the audio, establishing a focused "startup ritual" for the brain.
* **QA-Grade Reliability**: Engineered with a stability-first mindset, featuring low-level optimizations to bypass aggressive Android power management restrictions.

## 3. High-level Architecture
The project is built using **Clean Architecture** and **MVVM** patterns to ensure modularity and testability:
* **Trigger Layer**: Leverages `AlarmManager` and `BroadcastReceiver` to handle exact alarms in compliance with Android 12+ (API 31+) requirements.
* **Enforcement Service**: Launches a `Foreground Service` to maintain the highest system priority, preventing the app from being killed during active playback.
* **Audio Controller**: Interfaces with `AudioManager` to implement "Audio Enforcement," locking `STREAM_MUSIC` to a predefined gain (default: 60%).
* **Security Overlay**: Manages the Z-index and visibility logic via `WindowManager` to ensure the overlay persists across both Keyguard (lock screen) and unlocked states.
* **Fail-safe Watchdog**: Includes a 10-second monitoring mechanism; if the stream fails to load or network connectivity is lost, the system automatically switches to a local fallback audio resource.

## 4. How to Run
### Prerequisites
* Android Studio Ladybug | 2024.2.1 or later.
* Android SDK API 31+ (Android 12 or higher).
* A physical device with Spotify or YouTube installed (recommended for testing Intent resolution).

### Installation Steps
1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/panfactorytw/wonderwall-morning-android.git](https://github.com/panfactorytw/wonderwall-morning-android.git)
