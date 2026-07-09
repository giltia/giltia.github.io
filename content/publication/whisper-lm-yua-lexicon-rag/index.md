---
title: "Whisper-LM with a Maya Lexicon: Correcting Yucatec Maya ASR Transcriptions Using Gemini and a Dictionary as Reference"
authors:
- admin
date: "2026-07-09T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2026-07-09T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ["report"]

# Publication name and optional abbreviated publication name.
publication: "Technical notebook (Google Colab)"
publication_short: ""

abstract: We present a Google Colab notebook implementing a post-processing pipeline for automatic Yucatec Maya transcriptions generated with Whisper. Since Whisper does not support Yucatec Maya, its outputs are noisy and frequently misidentified as Spanish, English, or even Japanese. The pipeline combines three components; a rule-based orthographic normalizer grounded in Yucatec Maya morphology, a Maya–Spanish lexicon of 2,988 entries used as an RAG-style orthographic reference, and a language model (Gemini 2.0 Flash) that corrects the transcription without translating it. Evaluated on 1,010 audio segments with reference transcriptions, the system marginally reduces CER (1.074 → 1.073) and WER (1.180 → 1.169) relative to raw Whisper turbo output, highlighting both the potential and the limits of post-ASR correction when the underlying acoustic model does not know the language.

# Summary. An optional shortened abstract.
summary: A Google Colab pipeline that corrects noisy Whisper transcriptions of Yucatec Maya by combining morphological rules, a 2,988-entry lexicon, and Gemini 2.0 Flash as a corrector model.

tags:
- Yucatec Maya
- ASR
- Whisper
- Large Language Models
- Low-Resource Languages
featured: true

links: []
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Associated Projects (optional).
projects: []

# Slides (optional).
slides: ''
---

## What problem does this notebook address?

Whisper, OpenAI's automatic speech recognition (ASR) system, does not include Yucatec Maya among its supported languages. When transcribing Maya audio, the model produces very noisy output and frequently "detects" the wrong language: in our data, Maya segments were labeled as Spanish, English, and even Japanese. This notebook explores a practical question: **how much can a large language model (LLM) improve Whisper's output if we give it a Maya lexicon as reference?**

## Pipeline architecture

The full flow is:

```
Audio → Whisper (turbo) → Rule-based normalizer → Gemini + lexicon → Normalizer → Evaluation (CER/WER)
```

### 1. Input data

The starting point is a CSV file (`transcription_results41Turbo.csv`) with 1,010 audio segments already transcribed by Whisper turbo. Each row includes the human reference transcription (`original_transcription`), Whisper's prediction (`whisper_prediction`), the detected language, and initial metrics (chrF, WER, CER).

### 2. Maya lexicon as reference (RAG component)

A Maya–Spanish dictionary in TSV format (`yua_dictionary.tsv`) with **2,988 entries** is loaded. A `YuaLexicon` class provides exact lookup and fuzzy matching (via `difflib.get_close_matches`), making it possible to find the closest valid Maya word for a mis-transcribed token.

### 3. Rule-based orthographic normalizer

Before and after the LLM pass, the text is normalized with Yucatec Maya linguistic rules taken from a reference grammar:

- **Root morphology rules**: for example, *bin* (to go) with the irregular root *xi'* in the intransitive indefinite future, or positionals such as *chil*, *kul*, and *wa'al* that lose the *l* before *-tal*.
- **"Safe" regex patterns**: *bins* → *bis*, *taals* → *taas*, and verbs whose final *b* changes to a glottalized structure (*jáalk'ab* → *jáalk'a'a*).
- **Lexicon verification**: if the normalized form exists in the dictionary it is kept; if the original form was already valid, it is preserved.

### 4. Correction with Gemini (Whisper-LM)

Each normalized transcription is sent to **Gemini 2.0 Flash** with a prompt that includes up to 500 words from the Maya lexicon as an orthographic reference. The key prompt instructions are: correct the text following standard Yucatec Maya grammar and orthography, **do not translate into Spanish**, choose the most likely option according to the lexicon, and return only the corrected text.

### 5. Evaluation

Character error rate (CER) and word error rate (WER) are computed with `editdistance` against the human reference transcription:

| Metric | Whisper turbo | Whisper-LM (this pipeline) |
|--------|--------------|----------------------------|
| Mean CER | 1.0743 | 1.0725 |
| Mean WER | 1.1796 | 1.1692 |

## What did we learn?

The improvement is **marginal**: LLM post-processing with a lexicon recovers some orthographic form, but it cannot reconstruct information the acoustic model never captured. With CER/WER values above 1.0, Whisper's output is so far from the reference that text-level correction has little material to work with. The practical takeaway is that, for Yucatec Maya, **the bottleneck is the acoustic model**: what is needed is fine-tuning Whisper on Maya speech data, not just downstream correction.

## Next steps

- Fine-tune Whisper with transcribed Yucatec Maya audio.
- Extend the orthographic rules (`ORTHO_RULES`) with recurrent errors observed in the transcriptions.
- Grow the lexicon and experiment with selective retrieval (sending only the entries relevant to each segment to the prompt, instead of a fixed list).
