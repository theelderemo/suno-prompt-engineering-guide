# Core Concepts of Suno's AI

This document covers the fundamental principles of Suno's music generation model, based on an analysis of its style data. Understanding these concepts is the key to effective prompt engineering.

## Co-Occurrence and Genre Blending

[cite_start]Sunō does not generate music from a list of "pure" genre templates[cite: 14]. [cite_start]Instead, it blends different styles together based on known co-occurrence patterns found in its training data[cite: 14]. [cite_start]When you provide a prompt like "rap," the AI is statistically likely to "smuggle in" elements of `trap`, `hip hop`, `bass`, and `beat` because these styles are frequently associated with each other in the dataset[cite: 15].

[cite_start]For example, the connection between `rap` and `trap` is quantified at 327 billion, while its connection to `pop` is 13.7 billion[cite: 1, 16]. This statistical relationship is the primary driver of the final sound.

## The "Pop" Axis Mundi

[cite_start]Within Suno's dataset, "pop" acts as a central gravitational force[cite: 18]. [cite_start]Nearly every genre is strongly connected to and eventually gravitates toward pop sensibilities[cite: 14].

Here are some examples of this gravitational pull:
* [cite_start]`rock` has a 315 billion co-occurrence value with `pop`[cite: 3, 18].
* [cite_start]`funk` has a 116 billion co-occurrence value with `pop`[cite: 6, 18].
* [cite_start]`emo` has a 12.2 billion co-occurrence value with `pop`[cite: 4, 18].

[cite_start]Because of this, unless you explicitly exclude pop from your prompt, your generated track will likely carry pop mixing structures or hooks, even if it's labeled "metal" or "funk"[cite: 18].

## Metadata as Implicit Prompting

[cite_start]The style tags in Suno are not just decorative labels; they function as "soft prompts" that are baked into the model's latent conditioning[cite: 19]. [cite_start]Each style can be thought of as a vector in an embedding space[cite: 20]. [cite_start]The more often two tags appear together in the data, the stronger their vectors pull on each other[cite: 21].

[cite_start]This creates predictable blends[cite: 22]:
* [cite_start]Combining `dark` and `synth` will pull the output towards `synthwave`[cite: 22].
* [cite_start]Combining `emotional` and `piano` will pull the output towards ballad-style tracks[cite: 22].
* [cite_start]`female vocals` has a massive overlap with `pop` and `bass` but not with `rock` or `metal`[cite: 22].

## Genre Clouds and Entanglement

[cite_start]Because of the co-occurrence model, there are no clean genre boundaries[cite: 14, 23]. [cite_start]Styles are entangled with one another, forming what can be described as "genre clouds"[cite: 23].

Key genre clouds include:
* [cite_start]**Rap Cloud**: `rap` ↔ `trap` ↔ `bass` ↔ `hip hop` ↔ `beat` [cite: 23]
* [cite_start]**Orchestral Cloud**: `orchestral` ↔ `epic` ↔ `cinematic` ↔ `dramatic` ↔ `piano` [cite: 23]
* [cite_start]**Indie Cloud**: `indie` ↔ `pop` ↔ `acoustic` ↔ `dreamy` ↔ `psychedelic` [cite: 23]
* [cite_start]**Dark Electronic Cloud**: `dark` ↔ `synth` ↔ `electro` ↔ `synthwave` ↔ `futuristic` [cite: 23]

Understanding these clouds helps predict outcomes. [cite_start]For example, asking for "dreamy indie rock" will likely pull in soft synth textures from its neighboring styles, not just guitars[cite: 23].

## Style Glue: Beat, Bass, and Synth

[cite_start]Some tags are so ubiquitous that they act as "glue layers" across almost all styles[cite: 29]. [cite_start]These are `beat`, `bass`, and `synth`[cite: 29].

* [cite_start]`beat` appears in everything from `rap` to `country`[cite: 1, 5, 29].
* [cite_start]`bass` bridges genres like `trap`, `funk`, `electro`, and even `piano`[cite: 3, 5, 8, 29].
* [cite_start]`synth` quietly infects a wide range of styles, even at low levels[cite: 29].

[cite_start]These tags often act as latent, default components in the mix unless they are explicitly overwritten or excluded in a prompt[cite: 29].

## Feedback Loops and How to Break Them

[cite_start]The co-occurrence system can create feedback loops[cite: 30]. [cite_start]If users hear "rap" tracks that sound like "trap," they are more likely to tag them as `trap` in the future[cite: 29]. [cite_start]This action strengthens the `rap` ↔ `trap` co-occurrence even more, making it harder to generate other styles of rap[cite: 30].

[cite_start]To escape this loop and generate more unique sounds, you must prompt with dissonant pairings and weird specificity[cite: 31].