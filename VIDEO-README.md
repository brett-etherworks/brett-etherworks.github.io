# Self-Hosted Video Guide

## Overview

This guide explains how to use the HTML5 `<video>` tag to host videos directly on your server instead of using Vimeo or YouTube. This gives you full control over your content and branding.

**Benefits:**
- No third-party branding or ads
- Full control over player appearance
- Works with the brutalist design aesthetic
- Open web standards (no Flash!)

**Trade-offs:**
- You need to handle video hosting and bandwidth
- You're responsible for encoding and optimization
- No built-in analytics like YouTube provides

## Video Formats & Browser Compatibility

For maximum compatibility, provide videos in **multiple formats**:

### Recommended Format Strategy

1. **MP4 (H.264)** - Primary format, works everywhere
2. **WebM** - Smaller file sizes, good for modern browsers
3. **Poster Image** - Shows before video plays

Most modern browsers support MP4, so you can start with just that and add WebM later for optimization.

## Preparing Your Videos

### 1. Video Encoding Settings (for Performance)

Use a tool like **HandBrake** (free) or **FFmpeg** (command line) to optimize your videos:

**Recommended Settings:**
- **Resolution**: 1920x1080 (1080p) or 1280x720 (720p)
- **Frame Rate**: 24-30 fps (match your original footage)
- **Bitrate**: 
  - 1080p: 5-8 Mbps
  - 720p: 2.5-5 Mbps
- **Audio**: AAC, 128-192 kbps, stereo
- **Format**: MP4 (H.264 codec)

**Why these settings?**
- Lower bitrates = faster streaming
- H.264 is universally supported
- These sizes balance quality and performance

### 2. Using HandBrake (Free, GUI-based)

1. **Download HandBrake**: https://handbrake.fr
2. **Open your video file**
3. **Select Preset**: "Fast 1080p30" or "Fast 720p30"
4. **Adjust Quality**:
   - Go to "Video" tab
   - Set quality to RF 22-24 (lower = better quality but bigger file)
5. **Save**: Give it a clear filename like `metaverse-demo.mp4`

### 3. Using FFmpeg (Command Line, More Control)

Install FFmpeg: `brew install ffmpeg`

**Basic MP4 conversion:**
```bash
ffmpeg -i input.mov -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k output.mp4
```

**Create a web-optimized MP4:**
```bash
ffmpeg -i input.mov \
  -c:v libx264 \
  -crf 23 \
  -preset medium \
  -movflags +faststart \
  -vf scale=1920:1080 \
  -c:a aac \
  -b:a 128k \
  metaverse-demo.mp4
```

**What these flags mean:**
- `-crf 23`: Quality (18-28 range, 23 is good balance)
- `-preset medium`: Encoding speed vs compression
- `-movflags +faststart`: Enables streaming (critical!)
- `-vf scale=1920:1080`: Resize to 1080p
- `-b:a 128k`: Audio bitrate

**Create WebM version (optional, smaller file size):**
```bash
ffmpeg -i input.mov \
  -c:v libvpx-vp9 \
  -crf 30 \
  -b:v 0 \
  -c:a libopus \
  -b:a 128k \
  metaverse-demo.webm
```

### 4. Create Poster Images

A poster image shows before the video plays:

```bash
ffmpeg -i metaverse-demo.mp4 -ss 00:00:05 -vframes 1 metaverse-poster.jpg
```

This extracts a frame at 5 seconds into the video.

## HTML Video Tag Implementation

### Basic Video Tag (Recommended for Your Site)

Replace the current video container sections with:

```html
<div class="video-container">
    <video 
        controls 
        preload="metadata" 
        poster="videos/metaverse-poster.jpg"
        class="video-player">
        <source src="videos/metaverse-demo.mp4" type="video/mp4">
        <source src="videos/metaverse-demo.webm" type="video/webm">
        Your browser doesn't support HTML5 video. 
        <a href="videos/metaverse-demo.mp4">Download the video</a> instead.
    </video>
    <div class="video-caption">
        Documentation: Welcome to the Metaverse filter experience
    </div>
</div>
```

### Explanation of Attributes

- **`controls`**: Shows play/pause, volume, fullscreen buttons
- **`preload="metadata"`**: Loads only metadata (duration, dimensions), not the whole video
  - Alternative: `preload="none"` - loads nothing until user clicks (saves bandwidth)
  - Alternative: `preload="auto"` - starts loading video (not recommended)
- **`poster="..."`**: Image shown before playing
- **`class="video-player"`**: For custom styling

### Important: preload Options

**For your use case (wait until user clicks play):**

```html
<video controls preload="none" poster="videos/metaverse-poster.jpg">
```

**Preload options:**
- `none`: Best for bandwidth - nothing loads until play
- `metadata`: Good middle ground - loads duration/size info
- `auto`: Starts downloading - only use if you want autoplay-ish behavior

## CSS Styling (Already Compatible!)

Your existing `.video-container` CSS already works! Just need to add:

```css
.video-player {
    width: 100%;
    height: auto;
    display: block;
    background: #000;
}
```

Add this to your `styles.css` file after the existing video styles.

## File Organization

Create a folder structure like this:

```
your-website-folder/
├── index.html
├── metaverse.html
├── ursula.html
├── brainrot.html
├── styles.css
└── videos/
    ├── metaverse-demo.mp4
    ├── metaverse-demo.webm (optional)
    ├── metaverse-poster.jpg
    ├── ursula-demo.mp4
    ├── ursula-poster.jpg
    ├── brainrot-demo.mp4
    └── brainrot-poster.jpg
```

## Updated HTML for Each Case Study

### For metaverse.html:

```html
<div class="video-container">
    <video 
        controls 
        preload="none" 
        poster="videos/metaverse-poster.jpg"
        class="video-player">
        <source src="videos/metaverse-demo.mp4" type="video/mp4">
        Your browser doesn't support HTML5 video. 
        <a href="videos/metaverse-demo.mp4">Download the video</a>.
    </video>
    <div class="video-caption">
        Documentation: Welcome to the Metaverse filter experience
    </div>
</div>
```

### For ursula.html:

```html
<div class="video-container">
    <video 
        controls 
        preload="none" 
        poster="videos/ursula-poster.jpg"
        class="video-player">
        <source src="videos/ursula-demo.mp4" type="video/mp4">
        Your browser doesn't support HTML5 video. 
        <a href="videos/ursula-demo.mp4">Download the video</a>.
    </video>
    <div class="video-caption">
        Documentation: The Education of Ursula at Signals Festival (2024)
    </div>
</div>
```

### For brainrot.html:

```html
<div class="video-container">
    <video 
        controls 
        preload="none" 
        poster="videos/brainrot-poster.jpg"
        class="video-player">
        <source src="videos/brainrot-demo.mp4" type="video/mp4">
        Your browser doesn't support HTML5 video. 
        <a href="videos/brainrot-demo.mp4">Download the video</a>.
    </video>
    <div class="video-caption">
        Documentation: BrainRot Revolution at the Bay Centre
    </div>
</div>
```

## Performance & Streaming

### How Streaming Works

With `movflags +faststart` (or HandBrake's web optimization), the video file is structured so:
1. Metadata goes at the beginning of the file
2. Browser can start playing before entire file downloads
3. This is called "progressive download" or "pseudo-streaming"

**It's not true streaming** (like RTMP or HLS), but it works perfectly for most websites.

### File Size Guidelines

**Target file sizes (for reasonable load times):**
- Short clips (30 sec - 2 min): 10-30 MB
- Medium videos (2-5 min): 30-100 MB  
- Longer videos (5-15 min): 100-300 MB

**If your videos are larger:**
- Reduce resolution to 720p
- Increase CRF value (lower quality, smaller file)
- Trim unnecessary footage

### Testing Streaming

1. Upload video to your server
2. Open browser DevTools (F12 or Cmd+Option+I)
3. Go to Network tab
4. Play the video
5. You should see the video file loading in chunks, not all at once

## Hosting Considerations

### Where to Host

**Option 1: Same Server as Website**
- Pro: Simple, everything in one place
- Con: Uses your bandwidth, might be slow for users far away

**Option 2: CDN (Content Delivery Network)**
- Services: Cloudflare R2, Bunny CDN, AWS CloudFront
- Pro: Fast worldwide, cheaper bandwidth
- Con: Slightly more complex setup

**Option 3: Object Storage**
- Services: AWS S3, Backblaze B2, Digital Ocean Spaces
- Pro: Cheap storage, designed for media files
- Con: Need to set CORS headers correctly

### Bandwidth Estimation

**Example:**
- Video file: 50 MB
- 100 views per month = 5 GB bandwidth
- 1,000 views per month = 50 GB bandwidth

Most basic hosting plans include 100GB+ bandwidth, so you should be fine for moderate traffic.

## Advanced: Adaptive Streaming (Optional)

If your videos are very long or you expect high traffic, consider HLS (HTTP Live Streaming):

**Benefits:**
- Adjusts quality based on user's connection
- Better buffering
- More professional

**Trade-off:**
- Much more complex setup
- Requires encoding into multiple quality levels
- Need special server configuration or service

**Services that make HLS easy:**
- Cloudflare Stream (paid, but simple)
- Mux (developer-friendly)

For your dissertation site, basic HTML5 video is probably sufficient!

## Accessibility

Always include captions for accessibility:

```html
<video controls preload="none" poster="videos/metaverse-poster.jpg">
    <source src="videos/metaverse-demo.mp4" type="video/mp4">
    <track 
        label="English" 
        kind="subtitles" 
        srclang="en" 
        src="videos/metaverse-captions.vtt" 
        default>
</video>
```

### Creating VTT Caption Files

Simple text format:

```
WEBVTT

00:00:00.000 --> 00:00:05.000
Welcome! Blink if you agree to the terms and conditions!

00:00:05.000 --> 00:00:10.000
We're so excited you've agreed to join The Metaverse!
```

Save as `metaverse-captions.vtt`

Tools to help:
- YouTube's auto-captions → download as .srt → convert to .vtt
- Rev.com (paid transcription service)
- Subtitle Edit (free software)

## Quick Start Checklist

- [ ] Install HandBrake or FFmpeg
- [ ] Encode your videos to MP4 with web optimization
- [ ] Create poster images (one frame from each video)
- [ ] Create `videos/` folder in your website directory
- [ ] Add `.video-player` styles to `styles.css`
- [ ] Update HTML files with new `<video>` tags
- [ ] Test locally - videos should play without downloading fully
- [ ] Upload to your server
- [ ] Test on actual site with slower connection if possible

## Troubleshooting

**Video doesn't play:**
- Check file path is correct
- Make sure video is encoded with H.264
- Try opening video file directly in browser

**Video downloads instead of playing:**
- Server needs correct MIME types
- Add to `.htaccess`: `AddType video/mp4 .mp4`

**Video is choppy/slow:**
- File size too large - re-encode with higher CRF
- Reduce resolution to 720p
- Check you used `movflags +faststart`

**Video plays but doesn't stream:**
- You forgot `-movflags +faststart` in encoding
- Re-encode with that flag

## Example FFmpeg Complete Workflow

```bash
# 1. Create optimized MP4
ffmpeg -i original-footage.mov \
  -c:v libx264 \
  -crf 23 \
  -preset medium \
  -movflags +faststart \
  -vf scale=1920:1080 \
  -c:a aac \
  -b:a 128k \
  videos/metaverse-demo.mp4

# 2. Create poster image
ffmpeg -i videos/metaverse-demo.mp4 \
  -ss 00:00:05 \
  -vframes 1 \
  videos/metaverse-poster.jpg

# 3. Check file size
ls -lh videos/metaverse-demo.mp4
```

## Resources

- **HandBrake**: https://handbrake.fr
- **FFmpeg**: https://ffmpeg.org
- **FFmpeg Guide**: https://trac.ffmpeg.org/wiki/Encode/H.264
- **HTML5 Video**: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video
- **WebVTT Format**: https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API

---

**Remember:** Start simple with just MP4 + poster image. You can always optimize further later!
