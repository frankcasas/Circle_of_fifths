# Circle_of_fifths
Playable Circle of Fifths

# 🎵 Interactive Circle of Fifths

A fully interactive, browser-based music theory tool featuring a visual Circle of Fifths with chord playback, mode exploration, extended chords, and inversions — no libraries, no dependencies, pure Web Audio API.


---

## ✨ Features

### 🎡 Circle of Fifths
- All **12 keys** arranged by fifths in a multi-ring canvas diagram
- **7 chord rings** per key, rendered from tonic outward
- **Key signature ring** showing ♯/♭ counts in standard notation
- Color-coded by chord quality: **major** (blue) · **minor** (purple) · **augmented** (orange) · **diminished** (green)
- Click any segment to hear the chord and open the key's full panel

### 🎼 Three Scale Types
Switch between scale systems using the top tabs:

| Tab | Scale Type | Characteristic |
|-----|-----------|----------------|
| Natural Major | Ionian-based diatonic | Standard major key harmony |
| Harmonic Minor | Raised 7th degree | Exotic augmented 2nd interval |
| Melodic Minor | Raised 6th & 7th | Jazz/classical hybrid harmony |

### 🎹 Chord Scale Panel
For any selected key, see and play all **7 diatonic chords** with:
- Roman numeral degree labels (I, ii, iii°, IV+, etc.)
- Chord quality displayed per chord
- Individual chord playback on click
- **▶ Play chords** — sequences through all 7 chords with visual highlighting

### 🎸 Mode Explorer
All **7 modes** per scale type with pill selectors:

**Natural Major modes:**
Ionian · Dorian · Phrygian · Lydian · Mixolydian · Aeolian · Locrian

**Harmonic Minor modes:**
Harmonic Minor · Locrian ♯6 · Ionian ♯5 · Dorian ♯4 · Phrygian Dominant · Lydian ♯2 · Ultralocrian

**Melodic Minor modes:**
Jazz Minor · Dorian ♭2 · Lydian Augmented · Lydian Dominant · Mixolydian ♭6 · Locrian ♯2 · Altered

Each mode shows:
- **Mode Chord Scale** — all 7 diatonic chords from that mode's perspective, with mode-specific degree labels
- **Interval formula** — e.g. R · 2 · ♭3 · 4 · 5 · 6 · ♭7 · 8
- **Note strip** — all 8 scale tones, individually playable
- **▶ Mode chords** and **▶ Mode scale** playback buttons

### 🎵 Chord Explorer
Click **any chord** anywhere in the interface to open the Chord Explorer, which provides:

**Extensions** — select voicing complexity:
- Major: Triad → Dom 7 → Maj 7 → 9 → Maj 9 → 11 → Maj 11 → 13 → Maj 13
- Minor: Triad → m7 → mMaj7 → m9 → mMaj9 → m11 → m13
- Diminished: Triad → ø7 (half-dim) → °7 (fully diminished)
- Augmented: Triad → +7 → +Maj7

**Inversions** — all available inversions for the selected voicing:
- Root position, 1st inversion, 2nd inversion, 3rd inversion
- **Slash notation** updates automatically (e.g. `Cmaj7 / E`)
- Bass note highlighted in green among chord tones

**Chord Tones** — each individual note is playable, labeled with its interval

---

## 🔊 Synthesis Engines

All audio is synthesized in real time using the **Web Audio API** — no audio files, no samples.

| Timbre | Engine | Character |
|--------|--------|-----------|
| 🎹 Piano | Triangle wave oscillator | Warm, soft attack |
| 🌊 Soft | Sine wave oscillator | Pure, clean tone |
| 🎷 Organ | Sawtooth oscillator | Rich harmonics |
| 🎸 Guitar | **Karplus-Strong** physical modeling | Realistic plucked string; chords strum with slight per-string delay |
| 🎻 Strings | 3× detuned saws + LFO vibrato + slow bow attack | Lush orchestral ensemble feel |

### Karplus-Strong (Guitar)
Seeds a delay line buffer with white noise, then runs a decay-filtered feedback loop at the target pitch frequency. Each string in a chord is staggered by ~40ms for a natural strumming effect.

### Strings Synthesis
Three sawtooth oscillators slightly detuned (−8, 0, +8 cents) are passed through a lowpass filter for warmth. A 5.2 Hz LFO starts after 150ms to simulate a player's natural vibrato. A slow gain ramp (~280ms attack) imitates drawing a bow across strings.

---

## 🚀 Getting Started

### Option 1 — Open directly in browser
Just open the HTML file — no build step, no server required.

```bash
git clone https://github.com/yourusername/circle-of-fifths.git
cd circle-of-fifths
open index.html   # macOS
# or
start index.html  # Windows
```

### Option 2 — Serve locally (recommended for some browsers)
```bash
npx serve .
# or
python3 -m http.server 8080
```
Then open `http://localhost:8080`.

---

## 🗂 Project Structure

```
circle-of-fifths/
├── index.html        # Everything — self-contained single file
└── README.md
```

All logic, styles, and audio synthesis live in a single `index.html`. No frameworks, no build tools, no external dependencies.

---

## 🎓 Music Theory Reference

### Scale Degree Colors
| Color | Quality | Examples |
|-------|---------|---------|
| 🔵 Blue | Major | I, IV, V |
| 🟣 Purple | Minor | ii, iii, vi |
| 🟠 Orange | Augmented | ♭III+ (Harmonic Minor) |
| 🟢 Green | Diminished | vii°, ii° |

### Roman Numeral Conventions
- **Uppercase** (I, IV, V) = major chord
- **Lowercase** (ii, vi) = minor chord
- **° suffix** (vii°) = diminished
- **+ suffix** (III+) = augmented
- **Accidentals** (♭VII, ♯iv°) = chromatic alterations from the mode

### Chord Inversions — Quick Reference
| Name | Bass Note | Notation |
|------|-----------|---------|
| Root position | Root (1st) | C |
| 1st inversion | 3rd | C/E |
| 2nd inversion | 5th | C/G |
| 3rd inversion | 7th (if present) | Cmaj7/B |

---

## 🖥 Browser Compatibility

Works in any modern browser with Web Audio API support:

| Browser | Support |
|---------|---------|
| Chrome / Edge | ✅ Full |
| Firefox | ✅ Full |
| Safari | ✅ Full (iOS too) |
| Opera | ✅ Full |

> **Note:** Some browsers require a user gesture (click/tap) before audio context can start. The first chord click initializes the audio engine automatically.

---

## 🙏 Acknowledgements

- Music theory data based on standard Western harmony and modal theory
- Harmonic Minor and Melodic Minor mode names follow jazz and classical convention
- Karplus-Strong algorithm originally described by Kevin Karplus and Alex Strong (1983)
- Built with ❤️ and the Web Audio API

---

## 📄 License

MIT — free to use, modify, and share.
