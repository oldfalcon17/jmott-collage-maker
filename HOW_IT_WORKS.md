# How JMott's Collage Maker Works
### A Simple Guide for Everyone

---

## The Short Version

**JMott's Collage Maker works like a digital picture frame with slots.**

You pick a frame style (layout), drop your photos into the slots, and export. Everything happens right on your computer - your photos never leave your device, and you're always in control of where each photo goes.

---

## How It Actually Works

### Step 1: You Pick a Layout

Think of layouts like picture frame templates at a craft store. Each one has a fixed number of "slots" in specific positions:

```
┌─────────┬─────────┐     ┌─────────────────────┐
│         │         │     │                     │
│  Slot 1 │  Slot 2 │     │       Slot 1        │
│         │         │     │                     │
├─────────┼─────────┤     ├──────────┬──────────┤
│         │         │     │  Slot 2  │  Slot 3  │
│  Slot 3 │  Slot 4 │     │          │          │
│         │         │     └──────────┴──────────┘
└─────────┴─────────┘
   "Grid 2×2"              "Hero Top + 2 Bottom"
```

These layouts are **pre-designed** - the app knows exactly where each slot is, how big it is, and what shape it is.

### Step 2: Your Photos Go Into Slots

When you add photos, they get placed into these slots. The app:

1. **Looks at your photo's shape** (landscape, portrait, or square)
2. **Looks at the slot's shape**
3. **Fits the photo to fill the slot** (zooming/cropping as needed)

This is basic math - no AI, no guessing, no "smart" decisions. If your photo is wider than the slot, the sides get cropped. If it's taller, the top and bottom get cropped.

### Step 3: Everything Stays on Your Computer

When you click "Export," the app:

1. Creates a blank canvas (your chosen size, like 1080×1080)
2. Places each photo into its slot position
3. Applies any effects you chose (borders, filters, etc.)
4. Saves the final image to your computer

**No internet needed. No uploads. No cloud processing.**

---

## What Makes This "Deterministic"?

**Deterministic** means: *the same inputs always produce the same outputs.*

If you:
- Use the same layout
- Use the same photos
- Use the same settings

You'll get the **exact same collage every single time**. There's no randomness, no AI making different decisions each time.

### Why This Matters:

| You Want... | Deterministic Approach |
|-------------|----------------------|
| Consistency | Same layout = same result, always |
| Predictability | You know exactly what you'll get |
| Control | YOU decide where photos go |
| Speed | No waiting for "processing" |
| Privacy | Photos never leave your computer |

---

## How "AI/Smart" Collage Tools Work Differently

Many modern collage apps use AI or "smart" processing. Here's what that typically means:

### The AI Approach:

1. **You upload photos** → They go to a server (the cloud)
2. **AI analyzes your photos** → Detects faces, objects, "importance"
3. **AI decides placement** → Chooses which photo goes where
4. **AI adjusts cropping** → Decides what parts to show/hide
5. **Server creates collage** → Sends it back to you

### What AI Is Doing Behind the Scenes:

```
Your Photo → Upload to Cloud → AI Analysis:
                                 ├─ Face detection
                                 ├─ Object recognition  
                                 ├─ "Aesthetic" scoring
                                 ├─ Color analysis
                                 └─ Composition rules
                              → AI Decisions:
                                 ├─ "This photo should be bigger"
                                 ├─ "Crop here to show the face"
                                 ├─ "This photo is less important"
                                 └─ "Rearrange for better flow"
                              → Generate Result → Download
```

### The Tradeoffs of AI Processing:

| Feature | AI Tools | JMott's Collage Maker |
|---------|----------|----------------------|
| **Where photos go** | AI decides | You decide |
| **Cropping** | AI guesses "best" crop | You control zoom/position |
| **Privacy** | Photos uploaded to servers | Photos stay on your computer |
| **Internet needed** | Yes, always | No (works offline) |
| **Speed** | Wait for server processing | Instant preview |
| **Consistency** | Results may vary | Same every time |
| **Account required** | Usually yes | No |
| **Subscription** | Often required | One-time purchase |

---

## A Real-World Comparison

### Scenario: Making a Family Vacation Collage

**Using an AI Tool:**
1. Upload 8 vacation photos to their website
2. Wait for upload (depends on your internet)
3. AI analyzes and arranges them
4. You see the result - AI put the beach photo small in the corner
5. You wanted it big! Try to adjust...
6. AI rearranges everything when you change one thing
7. Export and download
8. Your photos now exist on their servers

**Using JMott's Collage Maker:**
1. Drag 8 photos into the app (instant, no upload)
2. Pick "8-Photo Grid" layout
3. See exactly where each slot is
4. Drag your beach photo to the big slot
5. Adjust zoom to show the best part
6. Export - done
7. Photos never left your computer

---

## When AI Tools Make Sense

AI collage tools can be useful when:

- ✓ You have hundreds of photos and want quick results
- ✓ You don't care exactly where each photo goes
- ✓ You're okay with photos being uploaded
- ✓ You want the AI to make creative decisions for you

## When JMott's Collage Maker Makes Sense

Our approach is better when:

- ✓ You want control over every photo's placement
- ✓ Privacy matters (sensitive/personal photos)
- ✓ You need consistent, reproducible results
- ✓ You work offline or have slow internet
- ✓ You don't want another subscription
- ✓ You know what you want and just need a tool to make it

---

## The Bottom Line

**JMott's Collage Maker is a tool, not an assistant.**

We don't try to guess what you want. We don't analyze your photos. We don't make decisions for you.

We give you:
- 101 professionally-designed layouts
- Simple controls to place and adjust photos
- Fast, private, local processing
- Predictable, consistent results

**You're the artist. We're just the picture frame.**

---

## Technical Details (For the Curious)

### How Layouts Are Defined

Each layout is simply a list of rectangles:

```
"4 │ Grid 2×2": {
    "slots": [
        (0, 0, 50, 50),      # Slot 1: top-left
        (50, 0, 50, 50),     # Slot 2: top-right
        (0, 50, 50, 50),     # Slot 3: bottom-left
        (50, 50, 50, 50)     # Slot 4: bottom-right
    ]
}
```

Each slot is: (x position, y position, width, height) as percentages.

### How Photos Are Placed

```
1. Get slot dimensions (e.g., 540×540 pixels)
2. Get photo dimensions (e.g., 4000×3000 pixels)
3. Calculate scale to fill slot (maintain aspect ratio)
4. Center the photo in the slot
5. Crop anything outside the slot boundaries
```

No machine learning. No neural networks. Just geometry.

### How Effects Are Applied

```
1. Start with placed photos
2. Apply per-image adjustments (brightness, contrast, etc.)
3. Apply borders and rounded corners
4. Apply global filter (if selected)
5. Add background color/gradient
6. Composite everything into final image
```

Standard image processing operations that have existed for decades.

---

## Privacy Commitment

Your photos are processed using these libraries:
- **Pillow (PIL)** - Standard Python image library
- **Tkinter** - Standard Python GUI library

Neither of these connect to the internet. Neither sends any data anywhere.

The only network connection the app makes is to verify your license key with Gumroad when you first activate (one-time, just sends the key, not your photos).

**Your photos stay on your computer. Period.**

---

*JMott's Collage Maker - You're in control.*
