# VLC Video Player Project Instructions

This document provides essential context for AI coding agents working in this codebase.

## Project Overview

A modern video streaming player built with Next.js that supports:
- HLS (M3U8) and DASH streaming protocols
- Multi-language audio tracks
- Mobile-responsive design with automatic layouts
- Integration with YouTube, Facebook, and Twitch streams
- CDN delivery with adaptive bitrate streaming

## Key Components

### Video Player
- HTML5-based video player with customizable interface
- Supports multiple streaming protocols (HLS/M3U8, DASH)
- Multi-audio track selection
- Custom branding (logos, colors, posters)

### Streaming Features
- Global CDN integration (50+ edge locations)
- Adaptive bitrate resolution for optimal playback
- Live-to-VOD transition support
- Real-time analytics for viewer metrics

### Security & Controls
- Geo-location based access control
- Stream authorization mechanisms
- Protection against unauthorized hosting

## Project Structure

```
.
├── src/              # Core application source
│   ├── components/   # React components including video player
│   ├── styles/       # Global styles and theme
│   └── lib/         # Utilities and helper functions
├── public/          # Static assets and streaming manifests
└── config/         # Configuration files for CDN, streaming etc.
```

## Development Workflow

1. Setup:
   ```bash
   npm install
   npm run dev
   ```

2. Key Commands:
   - `npm run dev` - Start development server
   - `npm run build` - Production build
   - `npm run test` - Run test suite
   - `npm run lint` - Code linting

## Coding Conventions

1. Components
   - Use functional components with hooks
   - Follow shadcn/ui patterns for consistency
   - Implement responsive design using Tailwind CSS

2. State Management
   - Use React context for global player state
   - Local component state for UI interactions

3. Error Handling
   - Graceful fallbacks for stream failures
   - Clear error messages for end users
   - Logging for debugging and analytics

## Integration Points

1. Streaming Services
   - YouTube API integration in `src/lib/youtube`
   - Facebook Live API in `src/lib/facebook`
   - Twitch streaming in `src/lib/twitch`

2. CDN Configuration
   - Edge location setup in `config/cdn.js`
   - Caching rules and TTL settings

3. Analytics
   - Real-time viewer tracking
   - Bandwidth usage monitoring
   - Stream quality metrics

## Testing Guidelines

1. Unit Tests
   - Test player controls and UI interactions
   - Verify stream loading and error states
   - Mock CDN and streaming service APIs

2. Integration Tests
   - End-to-end streaming tests
   - Cross-browser compatibility
   - Mobile responsiveness verification

## Common Patterns

1. Stream Loading
   ```javascript
   // Example of loading an M3U8 stream
   const loadStream = async (url) => {
     const player = await initPlayer();
     await player.loadSource(url);
     await player.attachMedia(videoElement);
   };
   ```

2. Error Handling
   ```javascript
   // Standard error handling pattern
   try {
     await loadStream(url);
   } catch (error) {
     logError(error);
     showFallbackContent();
   }
   ```

## Important Notes

- Always test with different network conditions
- Verify multi-language support when modifying player
- Consider CDN caching when updating stream configurations
- Maintain mobile-first responsive design