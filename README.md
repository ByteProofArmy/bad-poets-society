# Bad Poets Society – Poem Generator

This repository contains the code and notebooks for a small “bad poetry” generator, built for the **Bad Poets Society** assignment.  
The project has two main parts:

1. **Building an inspiring set of poems** (grouped by theme: love, nature, dream)  
2. **Generating new themed poems** using simple NLP + templates, and presenting selected poems with generative AI (images & audio).

---

## 1. Repository structure

```text
POEM_GENERATOR/
├─ .venv/                     # Local virtual environment (optional, not submitted)
├─ text2audio/                # Scripts / files for text-to-speech presentation
├─ text2image/                # Scripts / files for text-to-image presentation
├─ bad_poet_society.ipynb     # Main poem generator (spaCy + templates)
├─ poetry_inspiring_set.ipynb # Builds the inspiring set from online poems
├─ poems_love.txt             # Love-themed inspiring set
├─ poems_nature.txt           # Nature-themed inspiring set
├─ poems_dream.txt            # Dream-themed inspiring set
├─ the3_for_ai.txt            # Final 3 selected poems (one per theme) for AI presentation
```
## 2. Dependencies
The project is implemented in Python and uses Jupyter notebooks.

Main Python packages:

+ spacy

+ en_core_web_sm (spaCy English model)

+ lemminflect (verb inflection)

+ inflect (noun pluralization)

+ requests / BeautifulSoup (or similar, depending on how poems are fetched)

+ ipykernel, jupyter (for running notebooks)

#### Setup
```
# create and activate a virtual environment (optional)
python -m venv .venv
source .venv/bin/activate        # Linux / macOS
# .venv\Scripts\activate         # Windows

pip install spacy lemminflect inflect requests beautifulsoup4 jupyter
python -m spacy download en_core_web_sm
```

## Building the inspiring set

poetry_inspiring_set.ipynb

This notebook:

Fetches poems from online poetry websites
(e.g. Poetry Foundation / Poetry.net / PoemHunter, depending on availability and page structure).
The poems are only used for study and for building an inspiring set.

Cleans and organises poems into three broad styles:

Love – relationship, emotions, affection, heartbreak

Nature – landscapes, seasons, natural imagery

Dream – surreal, abstract, dream-like language

Saves the resulting text corpora into:

poems_love.txt

poems_nature.txt

poems_dream.txt

These three files form the inspiring set in the sense of Ritchie: they define the kind of language and imagery the system aims to imitate, without copying lines directly.

## 4. Generating poems

The notebook `bad_poet_society.ipynb` loads the three inspiring sets and:

- uses spaCy to extract nouns, adjectives and verbs for each theme (love, nature, dream),
- stores them in theme-specific word pools,
- fills simple line templates (e.g. `PRON + V + the + ADJ + N`) with random words from those pools,
- uses `lemminflect` and `inflect` to fix basic subject–verb agreement and plural nouns,
- assembles 6–10 lines into a poem and adds a simple title.

By changing the `theme` parameter and the random seed, the same generator can produce different “bad poems” in different styles.


## Selected poems for AI presentation

the3_for_ai.txt

During experimentation, many poems were generated for each theme.
From these, we manually selected one poem per theme that:

still felt like a “bad poet society” output (some weirdness, not fully grammatical),

but had enough coherent imagery to be meaningful.

The final choices are stored in the3_for_ai.txt:

Conscious create – dream theme

Permanent rip – love theme

Shiny peak – nature theme

These three poems are used as input to generative AI tools.

Presenting poems with generative AI

The project uses additional tools to present the selected poems:

text2image/
Contains prompts and/or scripts for text-to-image models (e.g. Stable Diffusion, DALL·E, Midjourney, Pollo AI, etc.).
Each poem is converted into a set of visual elements (time of day, objects, mood), and these are used to generate:

images that show the poem text, and

separate images that illustrate key poetic elements (e.g. beds, pools, orchids, topaz, thunder).

text2audio/
Contains prompts or scripts for text-to-speech tools (e.g. ElevenLabs, Speechify, etc.) to:

create spoken-word versions of each selected poem.

The goal is to treat presentation (visual / audio) as part of the creative system, enhancing the perceived value of the generated poems.

