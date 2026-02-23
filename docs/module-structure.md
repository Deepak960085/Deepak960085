# API / Module Structure (MVVM)

## 1) High-Level Layers

```text
Presentation (UI + ViewModels)
        ↓
Domain (UseCases + Entities)
        ↓
Data (Repositories + DataSources)
        ↓
Platform (ExoPlayer/AVPlayer, FS APIs, SQLite)
```

## 2) Proposed Package Layout (Flutter)

```text
lib/
  core/
    constants/
    errors/
    permissions/
    theme/
    utils/
  features/
    video/
      data/
        datasources/
        models/
        repositories/
      domain/
        entities/
        usecases/
      presentation/
        screens/
        widgets/
        viewmodels/
    audio/
      data/
      domain/
      presentation/
    files/
      data/
      domain/
      presentation/
    home/
      presentation/
  shared/
    widgets/
    services/
  main.dart
```

## 3) Core Modules

### 3.1 MediaScannerModule
**Responsibility**: Discover local media and keep index up to date.

- `scanAllMedia()`
- `scanPath(path)`
- `refreshIndex()`

### 3.2 VideoPlaybackModule
**Responsibility**: Handle video session lifecycle and controls.

- `openVideo(mediaId)`
- `play()`, `pause()`, `seekTo(ms)`
- `setPlaybackSpeed(rate)`
- `loadSubtitles(source)`
- `setScreenLock(enabled)`

### 3.3 AudioPlaybackModule
**Responsibility**: Manage queue-based audio playback.

- `playTrack(mediaId)`
- `playNext()`, `playPrevious()`
- `setShuffle(enabled)`
- `setRepeatMode(mode)`
- `attachNotificationControls()`

### 3.4 FileManagerModule
**Responsibility**: File browsing and operations.

- `listDirectory(path, sort)`
- `createFolder(path, name)`
- `rename(path, newName)`
- `copy(items, destination)`
- `move(items, destination)`
- `delete(items)`

### 3.5 ResumeStateModule
**Responsibility**: Persist/restore last positions.

- `savePosition(mediaId, positionMs)`
- `getPosition(mediaId)`
- `clearPosition(mediaId)`

## 4) Data Model (SQLite)

### `media_items`
- `id` (PK)
- `path`
- `name`
- `type` (video/audio)
- `duration_ms`
- `size_bytes`
- `modified_at`
- `folder_path`

### `playback_state`
- `media_id` (FK)
- `last_position_ms`
- `speed`
- `subtitle_path` (nullable)
- `updated_at`

### `playlists` (optional for MVP+)
- `id` (PK)
- `name`
- `created_at`

### `playlist_items` (optional for MVP+)
- `playlist_id` (FK)
- `media_id` (FK)
- `order_index`

## 5) State Management Contracts

- **ViewModel Inputs**: user intents (tap, gesture, search, sort).
- **ViewModel Outputs**: immutable UI state (`loading`, `success`, `error`).
- **Repository Contracts**: abstract data access for testability.
- **Services**: wrap platform APIs (player engine, notifications, file I/O).

## 6) Minimal Internal APIs

- `MediaRepository`
  - `Future<List<MediaItem>> getVideos(Sort sort)`
  - `Future<List<MediaItem>> getAudios(Sort sort)`
  - `Future<void> refresh()`

- `PlayerRepository`
  - `Future<void> open(MediaItem item)`
  - `Stream<PlaybackState> observeState()`
  - `Future<void> seek(int ms)`

- `FileRepository`
  - `Future<List<FileNode>> list(String path, Sort sort)`
  - `Future<void> execute(FileCommand cmd)`

## 7) Platform Integrations

- Android: ExoPlayer, MediaSession, NotificationCompat, Storage Access Framework.
- iOS (optional): AVPlayer, MPNowPlayingInfoCenter, FileManager APIs.
