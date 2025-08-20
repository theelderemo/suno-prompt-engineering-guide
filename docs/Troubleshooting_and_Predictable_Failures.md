# Troubleshooting and Predictable Failures

Ever wonder why your prompt for a specific genre blend didn't work as expected? The answer almost always lies in the data. \[cite\_start]Suno's failures are often predictable because they are a direct result of the statistical co-occurrence patterns in its dataset.

---

## Case Study: Why Your "Emo Metal" Sounds Like Emo Pop

\[cite\_start]A common frustrating experience is asking for "emo metal" and getting a track that sounds like an emotional pop-rock ballad\[cite: 24]. \[cite\_start]This happens because the tag `emo` is overwhelmingly connected to styles associated with ballads, not metal breakdowns.

Let's look at the data for `emo`:

```json
"emo": {
    "emotional": 341000000000,
    "pop": 12200000000,
    "rock": 870000000,
    "piano": 49000000,
    "rap": 4900000,
    "sad": 450000,
    "ballad": 45000
}
```

As shown, emo's strongest connections are to emotional, pop, rock, and piano. Conspicuously, **metal has no direct link shown** in the primary connections for emo.

The AI's "learned representation" of **emo** is therefore based on emotional ballads, not screamo. When you prompt for "emo metal," the emo tag pulls the output towards its strong pop and piano connections, while the metal tag struggles to find a foothold.

---

### How to Fix It

To get closer to a true "emo metal" sound, you need to fight against emo's natural gravitational pull by:

* **Excluding the defaults**: Use negative prompts to block the path to pop and ballads.
* **Reinforcing the metal side**: Add more tags related to the desired metal subgenre.

```md
# A prompt that will likely fail:
"emo metal"

# A better prompt with constraints and reinforcements:
"metalcore, screamo, post-hardcore, emo vocals, aggressive, heavy metal guitar, no pop, no piano, no ballads"
```

---

## Analyzing Genre Connections

Before you spend credits on a prompt, you can use the data in this repository's `/data` folder to predict its potential outcome.

**Steps to Analyze a Prompt:**

1. Identify the primary tags in your prompt (e.g., `experimental` and `jazz`).
2. Look up each tag in the `co_existing_styles.json` file.
3. Check their strongest connections.

* **experimental** is tightly connected to rock, electro, and funk. It is not strongly connected to true random noise music.
* **jazz** is strongly connected to pop, funk, and rock.

4. Find the overlap. Both tags connect to funk and rock. This means your `"experimental jazz"` prompt will likely lean towards art-rock or glitch-funk, rather than free jazz.
