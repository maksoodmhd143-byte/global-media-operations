# Production Pipeline

## Package contract
One daily package contains:
- research dossier with source ledger
- selected topic and editorial rationale
- 30-second scene-based script
- narration text and optional audio file
- poster/flyer
- vertical MP4 video
- thumbnail/cover where supported
- platform-specific copy for YouTube, Instagram, LinkedIn and Facebook
- captions/subtitles
- quality report
- publication record

## Suggested directory convention
```text
content/
  YYYY-MM-DD-topic-slug/
    research.md
    claims.csv
    script.md
    narration.txt
    audio/
    graphics/
      poster.png
      thumbnail.png
    video/
      final.mp4
      captions.srt
      preview-frames/
    platform-copy/
      youtube.md
      instagram.md
      linkedin.md
      facebook.md
    qa-report.md
    publish-record.json
```

## Free-first media tooling
- Remotion: React-based video composition; verify current commercial licence eligibility.
- FFmpeg: media processing.
- SVG/CSS: original graphics and layouts.
- Local or otherwise authorised TTS adapter: optional; verify language quality and licence.
- No paid image/video/voice service is assumed.

## Validation
- Verify output files exist and are non-empty.
- Probe video duration, resolution, frame rate, codecs and audio stream.
- Extract representative frames and inspect text, contrast, cropping and safe areas.
- Check subtitle timing against narration.
- Confirm no unlicensed or placeholder media.
