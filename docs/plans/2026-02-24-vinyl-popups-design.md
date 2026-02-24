# Vinyl Record Pop-up Site — Design

## Overview

A single-page interactive site featuring a spinning vinyl record that plays music, overlaid with obnoxious retro spam pop-up ads. The contrast between a clean modern page and deliberately ugly pop-ups creates a parody aesthetic.

## Tech Stack

- Vanilla HTML/CSS/JS (single `index.html`)
- GSAP (CDN) for animations
- No build tools or frameworks

## Page Layout

- White background with subtle noise texture
- User-provided vinyl record graphic centered vertically and horizontally
- Clean, minimal — the pop-ups provide all the visual chaos

## Vinyl Record

- User-provided graphic, centered on page
- Spins via GSAP infinite rotation (~3-4 seconds per revolution, linear ease)
- Click to play/pause music
- On pause: GSAP tweens rotation speed down over ~1 second for natural deceleration
- "Click to play" hint appears initially, fades after first interaction

## Audio Playback

- Hidden HTML5 `<audio>` element
- User drops MP3 into project folder, wired to the audio element
- The vinyl record is the only control — click to play/pause
- Spinning/stopped state communicates playback status
- First click handles browser autoplay restriction

## Pop-up System

### Timing & Behavior
- Pop-ups start ~5 seconds after music begins playing
- New pop-up every 5-8 seconds (randomized interval)
- Pool of ~9 unique pop-ups
- Maximum ~4-5 visible at any time
- Never two appearing at the exact same moment
- Stop spawning when music is paused; existing ones stay on screen

### Positioning
- Random position on screen, constrained to viewport
- Can overlap each other and the vinyl record

### Dismissal
- Classic "X" close button on each pop-up
- GSAP exit animation on close
- 3 persistent pop-ups reappear after 10-15 seconds at a new position

## GSAP Animations

### Vinyl Spin
- `gsap.to()` with infinite rotation, linear ease
- Deceleration tween on pause (~1 second)

### Pop-up Entrances (randomized per pop-up)
- Scale up from 0 with overshoot bounce
- Slide in from a random screen edge
- "Slam" in — fast scale with subtle screen shake (2-3px offset, ~200ms)

### Pop-up Exits
- Quick scale-down to 0 with fade
- Or "crumple" — shrink and rotate slightly

### Persistent Reappearance
- Fades back in at a new position after delay, like it's sneaking back

## Pop-up Content

Visual style: bright gradients, chunky borders, Comic Sans or similar, garish colors (hot pink, neon green, yellow). Some have fake flashing text.

### Pop-up Pool
1. "Congratulations! You are the 1,000,000th visitor! CLAIM YOUR PRIZE"
2. "Hot singles in your area are waiting!" with a fake blurry photo
3. "YOUR COMPUTER MAY BE AT RISK! Download Protection Now"
4. "Lose 30 pounds with this ONE WEIRD TRICK doctors hate!"
5. "FREE iPod Nano — Just click here!!!"
6. "URGENT: Your account has been compromised! Verify now"
7. "Make $5,000/week working from home! Click to learn how"
8. "Browser update required! [Download] [Remind me later]" (both buttons close)
9. "Congratulations! You've been selected for a $500 Walmart gift card!"

### Persistent Pop-ups (reappear after closing)
- #1 (1,000,000th visitor)
- #3 (computer at risk)
- #6 (account compromised)

### Fake CTA Buttons
- "CLAIM NOW", "DOWNLOAD", "YES!" — non-functional or spawn another pop-up

## Assets Required from User
- Vinyl record graphic (PNG with transparency, SVG, or similar)
- MP3 audio file
