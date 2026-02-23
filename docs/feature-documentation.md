# Feature Documentation

## 1. Product Boundaries

### 1.1 Goals
- Provide smooth local playback for video and audio files.
- Offer practical local file browsing and management.
- Keep app fully functional without internet.

### 1.2 Non-Goals
- Streaming or online content catalogs.
- Login/account features.
- Ads or monetization modules.

---

## 2. Video Playback

### 2.1 Supported Formats
- MP4, MKV, AVI, MOV, FLV, 3GP

### 2.2 Core Controls
- Play/Pause
- Forward/Rewind (button + double-tap gestures)
- Seek bar
- Playback speed (0.5x–2.0x)
- Brightness gesture (left side)
- Volume gesture (right side)
- Screen lock mode
- Subtitle support (SRT, ASS, SSA)

### 2.3 Advanced Behavior
- Hardware acceleration by default; fallback to software decode when required.
- Picture-in-Picture (PiP) support where OS allows.
- Auto-resume from last saved playback position.
- Optional background play toggle for video.

### 2.4 Resume Rules
- Save position every 5 seconds while playing.
- Save immediately on pause/background/exit.
- If remaining duration < 60 seconds, clear resume marker.

---

## 3. Audio Playback

### 3.1 Supported Formats
- MP3, AAC, WAV, FLAC, OGG

### 3.2 Core Controls
- Play/Pause
- Next/Previous
- Shuffle
- Repeat (Off / One / All)
- Playback speed

### 3.3 Background Integration
- Foreground service (Android) for robust background playback.
- Notification controls with seek and track navigation.
- Lock screen media controls.
- Optional equalizer integration.

---

## 4. File Management

### 4.1 Browsing
- Local storage browser with folder navigation.
- Entry points from Videos, Music, and Folders tabs.

### 4.2 File Operations
- Create, rename, delete folders.
- Move/copy files.
- Multi-select actions.
- Sort by name/date/size.
- Search files and folders.

### 4.3 Media Scan
- Auto scan on app startup + storage change events.
- Manual refresh action for each tab.
- Ignore hidden/system folders by default (configurable).

---

## 5. Permissions

- Storage/Media read access (platform-specific permission model).
- Write/manage permissions only when file operations require them.
- Notification permission for background playback controls.

---

## 6. UX and UI Principles

- Bottom navigation with 3 tabs: Videos, Music, Folders.
- Minimal friction from launch to playback (≤2 taps for recent items).
- Consistent player gestures and visual cues.
- Light/Dark themes with persistent user preference.

---

## 7. Quality Targets (MVP)

- Video startup latency: under 1 second for local files on reference devices.
- Zero playback crashes in 30-minute stress loop test.
- Media scan completion under 10 seconds for 1,000 mixed files (device-dependent benchmark).
- Resume accuracy within ±2 seconds.
