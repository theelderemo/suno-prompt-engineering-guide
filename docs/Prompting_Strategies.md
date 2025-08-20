# Prompting Strategies

This guide provides practical strategies for designing effective prompts in Suno. \[cite\_start]The core idea is to treat prompting as a "constraint game" where you strategically guide the AI away from its default tendencies\[cite: 26].

---

## 1. Avoid Gravity Wells

\[cite\_start]To achieve a unique sound, you should first identify and avoid the main "gravity wells" in Suno's dataset unless they are essential for your track. \[cite\_start]The most powerful gravity wells are `pop`, `bass`, and `beat`. These tags are so common that they can easily overpower more subtle styles.

**Example:**
\[cite\_start]A simple prompt like `"groovy rock"` might get pulled towards pop-rock because of the strong `rock` -> `pop` connection\[cite: 3].

* A prompt likely to be pulled towards pop:
  `"groovy rock, catchy"`

* A more constrained prompt to avoid the pop gravity well:
  `"groovy funk rock, 70s, psychedelic, no pop"`

---

## 2. Force Exclusions with Negative Prompts

Negative prompts are your most powerful tool for constraining the model\[cite: 28]. By explicitly telling the AI what *not* to include, you can block its path to the most common statistical associations and force it to find alternative interpretations of your prompt\[cite: 28].

**Use Cases:**

* **To get 90s boom-bap**: The default "rap" prompt will lean heavily towards "trap"\[cite: 15, 17]. You must force the exclusion of trap.

  ```
  "90s hip hop, boom bap beat, no trap"
  ```

* **To get non-pop metal**: Many metal subgenres can get diluted with pop or rock elements.

  ```
  "heavy metal, aggressive, powerful, no pop, no pop rock"
  ```

---

## 3. Use Rare Pairings and Contrast Stacking

To push the model into its most creative and weird corners, you can combine styles that have very weak or non-existent connections in the dataset. This forces the AI to interpolate between distant points in its embedding space, often resulting in novel sonic textures.

**Examples of Rare Pairings:**

* Combine a mood with an unrelated genre:
  `"emo industrial"`

* Combine an orchestral style with a modern beat-based one:
  `"cinematic phonk"`

* Combine two genres with very different instrumentation and rhythms:
  `"gospel math rock"`

---

## 4. Be Specific and Add Detail to Weak Tags

Some tags in the dataset are "weak," meaning they have low connection counts and are underrepresented\[cite: 34, 35]. When you use a weak tag alone, the model may misinterpret it or default to its nearest popular neighbor\[cite: 35].

**Weak Tags Include**: `opera`, `math rock`, `grunge`, `swing`\[cite: 34].

To get consistent results with these tags, you must support them with more powerful, related tags that clarify your intent.

**Example:**

* The tag `grunge` by itself might not be enough\[cite: 36].

  ```
  # A weak, potentially ambiguous prompt:
  "grunge"

  # A stronger, more specific prompt:
  "90s grunge rock, alternative rock, distorted electric guitar, raw vocals"
  ```
