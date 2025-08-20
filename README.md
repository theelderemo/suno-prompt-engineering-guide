# Suno Prompt Engineering Guide

An unofficial guide and community resource for mastering prompt engineering for the Suno music generation AI. This repository is dedicated to demystifying Suno's style model to help creators achieve the exact sound they want.

The insights here are derived from an analysis of Suno's style co-occurrence data. By understanding the statistical patterns that drive the AI, we can move from guesswork to intentional creation.

---

## Key Concepts: The TL;DR

Suno's style model can be understood through a few core principles:

### 1. A Probabilistic Style-Mesh

Suno doesn’t generate “pure” genre tracks; it blends styles based on how often they appear together in its data.

### 2. Pop & Beat at the Core

The "pop" and "beat" genres are gravitational centers that many other styles are pulled towards.

### 3. Style Gravity Wells

Certain popular tags act as defaults, influencing the final mix unless you provide specific constraints.

### 4. Favors Overlapping Co-occurrence

The model prefers to blend styles that are statistically joined at the hip, creating "genre clouds."

### 5. Manipulation is Key

You can control the output by strategically excluding tags, stacking contrasting styles, and chaining together rare pairs.

---

## How This Guide Works

This repository is structured to take you from theory to practice:

* **Core Principles**: Understand the fundamental mechanics of the AI.
* **Prompting Strategies**: Learn actionable techniques for crafting better prompts.
* **Data & Tools**: Explore the raw data yourself.
* **Lyric Assistant**: Get help writing lyrics for your songs.

---

## Core Principles of Suno's AI

### 1. Co-Occurrence Drives Everything

Suno blends styles based on known co-occurrence patterns. If you ask for "rap," the model will likely include "trap," "hip hop," "bass," and "beat" elements because they are statistically linked.

For instance, the data shows a massive connection between rap and trap:

```json
"rap": {
    "trap": 327000000000,
    "pop": 13700000000,
    "bass": 1090000000
}
```

This means getting a specific sub-genre like 90s boom-bap requires you to force it with additional prompts and exclusions (e.g., "no trap").

---

### 2. "Pop" is the Axis Mundi

Nearly every genre in the dataset eventually gravitates toward "pop." It functions as the default gravitational center of the model.

Note the strong pull towards pop across different genres:

* "rock" → "pop" (315B)
* "funk" → "pop" (116B)
* "emo" → "pop" (12.2B)

Unless you explicitly exclude it, your track will likely incorporate pop mixing structures or hooks.

---

### 3. Genre Entanglement and "Clouds"

There are no clean genre boundaries in Suno's model. Styles are entangled and form "genre clouds," or clusters of heavily interconnected tags.

* **Rap Cloud**: rap ↔ trap ↔ bass ↔ hip hop ↔ beat
* **Orchestral Cloud**: orchestral ↔ epic ↔ cinematic ↔ dramatic ↔ piano
* **Indie Cloud**: indie ↔ pop ↔ acoustic ↔ dreamy ↔ psychedelic
* **Dark Electronic Cloud**: dark ↔ synth ↔ electro ↔ synthwave ↔ futuristic

This means a prompt for "dreamy indie rock" will naturally pull in soft synth textures, not just guitars.

---

### 4. Why Some Prompts Fail (Predictably)

If your "emo metal" prompt sounds like emo pop, it's because of the data connections. The tag **emo** is far more connected to pop and piano than it is to metal.

* "emo" is more connected to:

  * "pop" (12.2B)
  * "piano" (49M)

* than to:

  * "metal" (zero—no direct link shown)

You’re not getting metal because emo’s learned representation is based on emotional ballads, not screamo breakdowns.

---

## Practical Prompting Strategies

### 1. Avoid Gravity Wells

If you want a unique sound, avoid common "gravity well" tags like **pop**, **bass**, and **beat** unless they are essential to your goal. These tags are ubiquitous and act as latent mix-style defaults.

```md
# Instead of this:
"80s rock"

# Try this for a less pop-influenced sound:
"80s hard rock, no pop, no synth"
```

### 2. Force Exclusions

Use negative prompts to carve out sonic space and prevent the model from defaulting to the most common connections.

```md
# To get boom-bap instead of trap:
"90s hip hop, boom bap, no trap"

# To get funk without a pop structure:
"70s funk, groovy, no pop hooks"
```

### 3. Use Rare Pairings & Contrast Stacking

Push the model into its more creative and unpredictable corners by combining tags that are rarely paired together. This forces it to find novel ways to blend styles.

```md
# Push the model into weirder corners
"emo industrial"
"orchestral phonk"
"math rock gospel"
```

### 4. Be Specific with Weak Tags

Tags like **grunge**, **math rock**, or **swing** have low connection counts and can be misinterpreted. To get consistent results, you need to clarify them with stronger, related tags.

```md
# This might be misinterpreted:
"grunge"

# This is safer and more specific:
"90s grunge rock, alternative rock, heavy metal"
```

---

## Lyric Writing Assistant

Need help writing lyrics for your Suno creations? VRSA is a custom AI lyric and poetry creator that can help you craft the perfect words to match your sound.

---

## Data & Tools

This repository contains the raw data files that this guide is based on:

* `/data/co_existing_styles.json`: The full dictionary of style co-occurrence values.
* `/data/default_styles.json`: A list of the default styles available.

Feel free to use this data to build your own analysis tools or visualizations.

---

## Contributing

This is a community project. If you have new insights, prompt examples, or corrections, please feel free to open an issue or submit a pull request.

---

## Disclaimer

This is an unofficial guide and is not affiliated with Suno. The information is based on data found in the publicly accessible client-side code and is intended for educational and research purposes. All rights to the original data and the Suno platform belong to Suno.
