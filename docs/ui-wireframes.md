# UI Wireframes (Low-Fidelity)

> Text wireframes to guide UI implementation. Final visual design can be produced in Figma.

## 1) App Shell + Bottom Navigation

```text
+------------------------------------------------+
| Custom Media Player                            |
+------------------------------------------------+
|                                                |
|                 [ Active Tab ]                 |
|                                                |
+------------------------------------------------+
|  Videos          Music          Folders        |
+------------------------------------------------+
```

## 2) Videos Tab

```text
+------------------------------------------------+
| Videos                              [Search 🔍] |
+------------------------------------------------+
| Sort: Name ▼   Filter: All ▼   Refresh ⟳       |
+------------------------------------------------+
| [Thumb]  Movie_A.mkv                            |
|         01:42:11    1.2 GB    1080p            |
|------------------------------------------------|
| [Thumb]  Clip_B.mp4                             |
|         00:03:20    120 MB    720p             |
|------------------------------------------------|
| [Thumb]  Lecture_C.avi                          |
|         00:48:55    560 MB    SD               |
+------------------------------------------------+
|  Videos          Music          Folders        |
+------------------------------------------------+
```

## 3) Video Player Screen

```text
+------------------------------------------------+
| < Back        File Name               ⋮ Menu   |
+------------------------------------------------+
|                                                |
|                [ Video Surface ]               |
|                                                |
|  (Brightness gesture left / Volume right)      |
|                                                |
+------------------------------------------------+
| 00:12:22  [======●-----------]  01:42:11       |
| <<10s  Play/Pause  10s>>   Speed  Subs  Lock   |
+------------------------------------------------+
```

### Video Overlay States
- **Locked mode**: only unlock icon visible.
- **Subtitle chooser**: embedded tracks + external file picker.
- **PiP mode**: system-level mini-player entry from menu/home action.

## 4) Music Tab

```text
+------------------------------------------------+
| Music                               [Search 🔍] |
+------------------------------------------------+
| Tabs: Tracks | Albums | Artists | Playlists    |
+------------------------------------------------+
| ♪ Track_01.mp3         03:42     [⋮]           |
| ♪ Track_02.flac        05:11     [⋮]           |
| ♪ Track_03.aac         02:54     [⋮]           |
|------------------------------------------------|
| Mini Player: Track_02     ◀  ⏯  ▶              |
+------------------------------------------------+
|  Videos          Music*         Folders        |
+------------------------------------------------+
```

## 5) Full Audio Player

```text
+------------------------------------------------+
| < Now Playing                         Queue ≡  |
+------------------------------------------------+
|               [ Album Art ]                    |
|                                                |
|            Song Title - Artist                 |
|                                                |
|    Shuffle   Prev   Play/Pause   Next  Repeat  |
|                                                |
| 00:45   [=====●---------------]   03:42        |
| Speed 1.0x                Equalizer (Optional) |
+------------------------------------------------+
```

## 6) Folders Tab / File Manager

```text
+------------------------------------------------+
| Folders                             [Search 🔍] |
+------------------------------------------------+
| /storage/emulated/0/Movies                    |
+------------------------------------------------+
| 📁 Series/                                      |
| 📁 Downloads/                                   |
| 🎬 Film_X.mp4                                   |
| 🎵 Podcast_Y.mp3                                |
|------------------------------------------------|
| [New Folder] [Multi-Select] [Sort ▼] [Refresh] |
+------------------------------------------------+
|  Videos          Music          Folders*       |
+------------------------------------------------+
```

## 7) Multi-Select Action Bar

```text
+------------------------------------------------+
| 3 selected                         Cancel ✕    |
+------------------------------------------------+
| Move | Copy | Delete | Rename | Share          |
+------------------------------------------------+
```

## 8) Theme Notes
- Support light and dark mode with identical information architecture.
- Ensure gesture indicators and subtitles remain readable in both themes.
