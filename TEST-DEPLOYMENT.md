# La Habra Early Settlers - QR Test Deployment Guide

## What This Is

A **single-video prototype** to test the client's "QR code + personal device + earpiece" concept before building the full 24-video experience.

---

## Files Created

| File | Purpose |
|------|---------|
| `settlers-test.html` | Mobile-optimized video landing page |
| `qr-settlers-test.png` | QR code (links to file above) |
| `TEST-DEPLOYMENT.md` | This guide |

---

## Quick Setup (5 Minutes)

### Step 1: Place the Files

The test page references the video at a **relative path**. For the QR code to work, the page needs to be served via HTTP (not opened as `file://`).

**Option A: Local Testing (Same Device)**
```
Just open settlers-test.html directly in your browser.
```

**Option B: Museum WiFi (Recommended for Client Demo)**

If you have a local server or can host on the museum's network:

1. Upload entire `LaHabra-Vue` folder to the server
2. The QR code points to `settlers-test.html` — update it if the URL changes

**Option C: Quick Local Server (For Immediate Testing)**

```bash
# In the LaHabra-Vue directory:
python3 -m http.server 8000
```

Then the page is at `http://your-ip:8000/settlers-test.html`

---

### Step 2: Print the QR Code

The file `qr-settlers-test.png` is ready to print.

**Recommended:** Print at **2"x2" minimum** for reliable scanning. Larger is better for older users.

**Pro tip:** Laminate or place in a sleeve — museum environments have handling wear.

---

### Step 3: Position in Museum

**Suggested Placement:**

```
┌────────────────────────────────────┐
│                                    │
│   [ Early Settlers Exhibit ]       │
│                                    │
│   [ QR Code Placard Below ]        │
│                                    │
│   "Scan to hear the story"         │
│                                    │
└────────────────────────────────────┘
```

**Height:** Eye level for average adult (about 60" from floor)
**Lighting:** Avoid glare on QR code surface

---

## User Flow (What Visitors Experience)

1. **Scan QR code** with phone camera (iOS/Android both work)
2. **Tap notification** to open the page
3. **See earpiece prompt** — "For the Best Experience, Please Use Earbuds"
4. **Tap "I Have Earbuds"** (or "Skip This Step")
5. **Video loads** — full screen, mobile-optimized
6. **Tap play** (if autoplay blocked) or video starts automatically
7. **Watch with audio** through earbuds
8. **Screen stays awake** during playback (Wake Lock API)

---

## What to Watch For (Client Test Observations)

| Question | What to Observe |
|----------|-----------------|
| **Scan success rate** | Do phones instantly recognize the QR code? |
| **Load time** | How long does video take to start on cellular vs WiFi? |
| **Earpiece compliance** | Do visitors actually use earbuds, or skip? |
| **Audio clarity** | Can they hear narration clearly in museum acoustics? |
| **UX friction** | Where do they hesitate or look confused? |
| **"Modern" feel** | Does this match what they imagined? |

---

## Client Conversation Starters

After they experience it, ask:

1. _"Is this what you pictured when you said 'modern'?"_
2. _"Would your typical visitor (often 60+) find this intuitive?"_
3. _"Should we add more context before the video, or keep it minimal?"_
4. _"Do you want analytics — know how many people scan each code?"_
5. _"What would make you say 'yes, build all 24 like this'?"_

---

## Technical Notes

### Video File
- **Path:** `videos/government/La Habra Early Settlers.mp4`
- **Format:** MP4 (H.264 + AAC) — universally compatible
- **Size:** ~50MB (estimate) — acceptable for cellular, but WiFi is smoother

### Browser Compatibility
| Feature | iOS Safari | Android Chrome |
|---------|------------|----------------|
| QR scanning | ✅ Native | ✅ Native (or Google Lens) |
| Video playback | ✅ | ✅ |
| Wake Lock API | ✅ iOS 16.4+ | ✅ |
| Autoplay | ⚠️ Requires interaction | ⚠️ Requires interaction |

### If Autoplay Fails
The video has visible controls. Users can tap ▶️ manually. This is expected behavior — browsers block unmuted autoplay.

---

## Scaling to 24 Videos (When Ready)

Each video gets:
1. Its own HTML page (copy `settlers-test.html`, change title + video path)
2. Its own QR code (regenerate with that page's URL)
3. Consistent placement (same height, same placard design)

**Estimated effort:** ~30 minutes per video (mostly QA testing)

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| QR code won't scan | Make sure it's printed large enough (2" min). Check lighting. |
| Video won't load | File path is relative — ensure HTML and videos folder are together |
| Audio too quiet | Museum may be noisy. Consider captions or volume boost in post. |
| Page won't load on cellular | Video is ~50MB. Consider compression or WiFi-only placement. |
| Older users confused | Add larger text on placard: "1. Open Camera 2. Point 3. Tap" |

---

## Next Steps After Test

1. **Gather feedback** from client + 5-10 real visitors
2. **Iterate** on the design (colors, text, flow)
3. **Decide:** Build all 24, or adjust the concept first
4. **If yes:** I'll generate the full set with consistent branding

---

**Files Location:** `/Users/ben/Documents/Work/LaHabra-Vue/`

**Test page:** `settlers-test.html`
**QR code:** `qr-settlers-test.png`
**Video:** `videos/government/La Habra Early Settlers.mp4`

---

_Ruflo Queen Status: Test prototype ready for client demo._
