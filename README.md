# Custom Media Player Clone

This repository contains the product and technical blueprint for a local-only media player inspired by MX Player, focused on:

- High-performance **video playback**
- Full-featured **audio playback**
- Practical **local file management**

## Deliverables Included

- UI Wireframes (`docs/ui-wireframes.md`)
- Feature Documentation (`docs/feature-documentation.md`)
- API/Module Structure (`docs/module-structure.md`)
- Development Timeline (`docs/development-timeline.md`)

## Scope Summary

### Included
- Local media scanning (video/audio)
- Playback controls and gestures
- Subtitle support
- Folder browsing and file actions
- Offline-first metadata persistence

### Excluded
- Streaming
- Online content discovery
- User accounts/login
- Ads integration

## Suggested Baseline Stack

- **Framework**: Flutter (single codebase for Android-first, iOS optional)
- **Playback Engine**: ExoPlayer bridge on Android, AVPlayer bridge on iOS
- **Architecture**: MVVM + Repository pattern
- **Database**: SQLite (`sqflite`) for media index, resume positions, and playlists
