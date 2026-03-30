# NewPipe YouTube Features Documentation

This document outlines all YouTube-related features, buttons, screens, and how they work in the NewPipe Android app.

## Overview
NewPipe is a libre, lightweight streaming front-end for Android that supports multiple services, with YouTube being the primary and best-supported service. It fetches data from YouTube's API or parses the website without requiring a Google account.

## Main Screens and Navigation

### 1. Main Screen (Home)
- **Description**: The main entry point with a tabbed interface and navigation drawer.
- **Tabs** (configurable, defaults to):
  - **Trending/Home**: Shows trending videos from YouTube's default kiosk.
  - **Feed**: Displays videos from subscribed channels.
  - **Subscriptions**: Lists subscribed channels.
  - **Bookmarks**: Shows bookmarked playlists and channels.
- **Navigation Drawer Items**:
  - Subscriptions
  - Feed
  - Bookmarks
  - Downloads
  - History
  - Settings
  - Donation
  - About
- **Top Bar Buttons**:
  - Search button (magnifying glass icon)

### 2. Search Screen
- **Access**: From main screen search button or drawer.
- **Features**:
  - Search videos, channels, playlists
  - Filter by content language (YouTube-specific)
  - Search suggestions
- **How it works**: Uses YouTube's search API or website parsing to fetch results.

### 3. Video Detail Screen
- **Access**: Tapping on any video from lists/search.
- **Components**:
  - Video player
  - Title, uploader, view count, upload date
  - Like/dislike buttons (simulated)
  - Subscribe button
  - Download button
  - Share button
  - Add to playlist button
  - Description (expandable)
  - Comments section (toggleable)
  - Related videos (toggleable)
- **Player Features**:
  - Full screen toggle
  - Playback controls (play/pause, seek)
  - Quality selection (up to 4K)
  - Speed control
  - Subtitles toggle
  - Background audio mode
  - Popup/Picture-in-Picture mode

### 4. Channel Screen
- **Access**: From search results or video uploader link.
- **Features**:
  - Channel banner and info
  - Subscribe/unsubscribe button
  - Channel videos, playlists, about tabs
- **How it works**: Fetches channel data from YouTube API.

### 5. Playlist Screen
- **Access**: From search or channel playlists.
- **Features**:
  - Playlist videos list
  - Play all button
  - Add to local playlist
  - Download playlist

### 6. Downloads Screen
- **Access**: From navigation drawer.
- **Features**:
  - List of downloaded videos/audio
  - Playback controls
  - Delete downloads
  - Download settings

### 7. History Screen
- **Access**: From navigation drawer.
- **Features**:
  - Watch history
  - Search within history
  - Clear history

### 8. Settings Screen
- **Access**: From navigation drawer.
- **Categories**:
  - Appearance
  - Content
  - Downloads
  - History
  - Video/Audio
  - ExoPlayer
  - Notifications
  - Backup/Restore

## Core Features

### Video Playback
- **Resolutions**: Up to 4K
- **Formats**: MP4, WebM, etc.
- **How it works**: Parses YouTube's streaming data to get direct video URLs, uses ExoPlayer for playback.

### Audio Playback
- **Background Mode**: Continues playing when app is minimized
- **How it works**: Downloads only audio stream to save data, uses Android's media session.

### Live Streams
- **Support**: HLS streams
- **How it works**: Handles live stream URLs from YouTube.

### Search
- **Types**: Videos, channels, playlists
- **Filters**: Content language for YouTube
- **How it works**: Queries YouTube search API or parses search results.

### Subscriptions
- **No Account Required**: Local subscriptions stored in app database
- **Features**: Subscribe/unsubscribe, channel groups, notifications
- **How it works**: Stores channel IDs locally, periodically checks for new videos.

### Feed
- **Content**: Videos from subscribed channels
- **Grouping**: By channel groups
- **How it works**: Aggregates videos from subscribed channels.

### Local Playlists
- **Creation**: Create custom playlists
- **Management**: Add/remove videos, reorder
- **How it works**: Stored in local SQLite database.

### Downloads
- **Formats**: Video, audio, subtitles
- **Quality**: User-selectable
- **How it works**: Downloads streams to device storage.

### Comments
- **Display**: Toggleable in video detail
- **Features**: Nested comments, load more
- **How it works**: Fetches from YouTube API.

### Notifications
- **Types**: New video notifications from subscribed channels
- **Settings**: Enable/disable per channel or globally
- **How it works**: Background service checks for new videos.

### YouTube-Specific Features
- **Restricted Mode**: Option to enable YouTube's restricted mode which hides potentially mature content
- **Import Subscriptions**: Import YouTube subscriptions from Google Takeout (CSV/JSON)
- **YouTube Music Premium Handling**: Detects and shows message for premium-only content
- **Share as Temporary Playlist**: Share local playlists as temporary YouTube playlists
- **Content Language Filtering**: Search with specific content language for YouTube

## Buttons and Controls

### Video Item Buttons (in lists)
- Play button
- Channel name (navigates to channel)
- Menu button (options: download, add to playlist, share, etc.)

### Video Detail Buttons
- Play/Pause
- Full screen
- Quality selector
- Speed selector
- Subtitles toggle
- Background audio
- Popup mode
- Download
- Share
- Add to playlist
- Subscribe
- Like/Dislike
- Comments toggle
- Related videos toggle
- Description toggle

### Video Detail Buttons
- Play/Pause
- Full screen
- Quality selector
- Speed selector
- Subtitles toggle
- Background audio
- Popup mode
- Download
- Share
- Add to playlist
- Subscribe
- Like/Dislike
- Comments toggle
- Related videos toggle
- Description toggle
- Open in browser
- Play with Kodi

### Player Controls
- Seek bar
- Volume controls
- Brightness controls (in fullscreen)
- Lock screen controls
- Quality selection
- Audio track selection
- Playback speed control
- Subtitle selection
- Resize options
- Live sync (for live streams)
- Repeat mode
- Shuffle mode
- Previous/Next track
- More options menu
- Share
- Fullscreen toggle
- Close player
- Mute toggle

## How It Works Technically

### Data Extraction
- Uses NewPipe Extractor library (separate repository)
- Parses YouTube website HTML and API responses
- Extracts video streams, metadata, comments, etc.
- Handles YouTube's changing APIs and anti-bot measures

### Streaming
- Extracts direct video/audio URLs from YouTube's player data
- Supports DASH (Dynamic Adaptive Streaming over HTTP) for adaptive quality
- Handles HLS (HTTP Live Streaming) for live streams
- Uses ExoPlayer for playback with custom data sources

### Privacy and No Account Required
- No Google account needed
- No tracking or data collection
- Local storage only for user preferences and subscriptions
- Uses YouTube's public APIs and website parsing

### Background Processing
- Notification service checks for new videos from subscriptions
- Download service handles background downloads
- Audio service maintains playback when app is closed

### Error Handling
- Handles HTTP 403 errors (IP bans, geo-restrictions)
- Manages age-restricted content
- Deals with YouTube API changes and deprecation

This documentation covers all major YouTube-related features in NewPipe. The app is designed to provide a privacy-focused, account-free YouTube experience on Android.