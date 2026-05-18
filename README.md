<div align="center">

# AudioEditSurvey

### Audio Editing in the Era of Foundation Models: A Survey

[![Survey](https://img.shields.io/badge/Survey-Audio%20Editing-blue)](#)
[![Paper](https://img.shields.io/badge/Paper-Coming%20Soon-lightgrey)](#)
[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

</div>

---

# Quick Start

1. [Introduction](#introduction)  
2. [Scope](#scope)  
3. [Overall](#overall)  
   - [Organization of This Survey](#organization-of-this-survey)  
   - [Taxonomy of Audio Editing](#taxonomy-of-audio-editing)  
   - [Representative Audio Editing Methods](#representative-audio-editing-methods)  
4. [Foundation Models for Audio Editing](#foundation-models-for-audio-editing)  
5. [Training-based Audio Editing](#training-based-audio-editing)  
6. [Training-free Audio Editing](#training-free-audio-editing)  
7. [Resources](#resources)  
   - [Available Datasets](#available-datasets)  
   - [Data Tools](#data-tools)  
   - [Evaluation Protocols and Benchmarks](#evaluation-protocols-and-benchmarks)  
8. [Systemization Challenges and Future Directions](#systemization-challenges-and-future-directions)  
9. [Citation](#citation)

# What's New

- **2026.5.18:** The paper and full paper list will be updated soon.

---

## Introduction

This repository maintains the project page and paper list for **AudioEditSurvey: Audio Editing in the Era of Foundation Models**.

> **Abstract**  
> Audio editing aims to modify a given synthetic or real-world audio signal to meet users' specific needs. As a promising yet challenging direction in AIGC, it has attracted increasing attention in recent years. With the rapid progress of text-to-audio and text-to-speech generation, powerful audio generation models have become the primary foundation for modern audio editing systems. In this survey, we provide a comprehensive review of foundation-model-based audio editing. We first define the scope of audio editing from a unified perspective and present a detailed taxonomy of existing editing tasks. We then summarize the major foundation-model paradigms for audio editing, and review representative approaches from both training-based and training-free perspectives. In addition, we systematically discuss related resources, including datasets, data construction tools, and evaluation protocols. Finally, we identify open challenges in this field and outline promising directions for future research.

---

## Scope

This survey focuses on works that make direct contributions to **audio editing in the era of foundation models**. We define audio editing as modifying the acoustic attributes, instances, or semantic content of an existing audio recording, without transformations so substantial that they amount to generating an entirely new audio sample.

Accordingly, this survey mainly includes methods that rely on mainstream audio foundation model paradigms. We do not aim to comprehensively cover pure audio generation, signal-processing-based editing workflows, or spatial audio editing.

---

## Overall

### Organization of This Survey


Figure 1: Organization of the survey.

The survey is organized around four main perspectives: **editing tasks**, **foundation-model architectures**, **learning paradigms**, and **resources**. It first introduces the scope and taxonomy of audio editing, then reviews foundation-model paradigms and representative methods from both training-based and training-free perspectives, and finally summarizes datasets, data construction tools, evaluation protocols, and future challenges.

### Taxonomy of Audio Editing


Figure 2: A high-level taxonomy of audio editing.

To systematically organize audio editing in the foundation-model era, we categorize existing tasks according to the primary layer of audio information edited by the model. The taxonomy contains three representative categories:

| Category | Definition | Representative Editing Goals |
|---|---|---|
| Acoustic Editing | Modifies low-level perceptual attributes while preserving the overall structure and source characteristics of the original audio. | restoration, reverberation editing, loudness/mixing control, equalization, spectral texture editing |
| Semantic Editing | Modifies high-level interpretable information conveyed by audio while maintaining task-irrelevant properties. | linguistic editing, expressive editing, stylistic editing |
| Instance Editing | Manipulates identifiable audio entities while preserving the remaining scene and source relationships. | replacement, deletion/extraction, insertion, overlay/remixing |

### Representative Audio Editing Methods

| Model | Category | Paper URL |
|---|---|---|
| FluentSpeech | Training-based / Diffusion | https://arxiv.org/abs/2305.13612 |
| VoiceCraft | Training-based / Codec | https://arxiv.org/abs/2403.16973 |
| uSee | Training-based / Diffusion | https://arxiv.org/abs/2310.00900 |
| SpeechX | Training-based / Codec | https://arxiv.org/abs/2308.06873 |
| CosyEdit | Training-based / Codec | https://arxiv.org/abs/2601.05329 |
| AUDIT | Training-based / Diffusion | https://arxiv.org/abs/2304.00830 |
| SAO-Instruct | Training-based / Diffusion | https://arxiv.org/abs/2510.22795 |
| Non-Rigid Prompt Edit | Training-based / Diffusion | https://arxiv.org/abs/2310.12858 |
| InstructME | Training-based / Diffusion | https://arxiv.org/abs/2308.14360 |
| Instruct-MusicGen | Training-based / Codec | https://arxiv.org/abs/2405.18386 |
| AST | Training-free / Diffusion | https://arxiv.org/abs/2604.16056 |
| EdiTTS | Training-free / Diffusion | https://arxiv.org/abs/2110.02584 |
| DDPM Inversion | Training-free / Diffusion | https://arxiv.org/abs/2402.10009 |
| AudioEditor | Training-free / Diffusion | https://arxiv.org/abs/2409.12466 |
| PPAE | Training-free / Diffusion | https://arxiv.org/abs/2406.04350 |
| AudioMorphix | Training-free / Diffusion | https://arxiv.org/abs/2505.16076 |
| MelodyFlow | Training-free / Flow | https://arxiv.org/abs/2407.03648 |
| MEDIC | Training-free / Diffusion | https://arxiv.org/abs/2407.13220 |
| MusicMagus | Training-free / Diffusion | https://arxiv.org/abs/2402.06178 |
| MusRec | Training-free / Flow | https://arxiv.org/abs/2511.04376 |

---

## Foundation Models for Audio Editing

### 1. Early Neural Editing Models

Before the foundation-model era, early neural editing methods mainly explored task-specific generative models for local reconstruction and attribute control. Although limited in scale and generalization, these methods introduced core ideas such as local generation, context-aware reconstruction, boundary consistency, and attribute-conditioned editing.

### 2. Token-based Codec Language Models

Token-based codec language models cast audio editing as conditional generation over discrete audio tokens. After continuous audio is converted into compact token sequences, target regions can be edited through continuation, infilling, or selective regeneration conditioned on context, prompts, or task controls.

Key topics include:

- neural codec and discrete audio tokenization;
- semantic and acoustic token modeling;
- span-level infilling and selective regeneration;
- speech content editing and speaker-conditioned infilling;
- context preservation under codec compression.

### 3. Diffusion and Flow-Matching Models

Diffusion and flow-matching models formulate audio editing as conditional transformation in continuous acoustic spaces, such as mel-spectrograms or audio latents. They modify audio through conditional denoising, latent inversion, or continuous flow transformation, making them suitable for high-fidelity reconstruction, region-level refinement, and fine-grained acoustic control.

Key topics include:

- latent diffusion for audio editing;
- conditional denoising and source-conditioned regeneration;
- mask- and region-based local editing;
- latent inversion for real-audio editing;
- flow matching for efficient continuous audio transformation.

### 4. Audio Editing Interfaces

Instruction-conditioned and multimodal interfaces provide high-level control for foundation-model-based audio editing. They allow users to specify editing intents through natural language instructions, task prompts, reference audio, temporal regions, or visual cues, which are then translated into target spans, task embeddings, event locations, speaker references, or preservation constraints.

---

## Training-based Audio Editing

Training-based approaches learn editing behavior from supervised pairs, pseudo-pairs, or instruction-based triplets before inference. These methods explicitly optimize editing objectives, condition following, and preservation constraints, enabling stable and controllable editing.

| Paradigm | Description | Representative Scope |
|---|---|---|
| Task-specific Training | Optimizes models for predefined editing functions or domains. | text-based speech editing, prosody correction, source separation, music stem separation |
| Reference- and Attribute-based Training | Specifies the editing direction through reference audio, style examples, or attribute labels. | voice conversion, timbre transfer, emotion editing, mixing style transfer |
| Instruction-conditioned Training | Learns from instruction-input-output triplets to follow natural-language editing requests. | addition, deletion, replacement, inpainting, super-resolution, music remixing, expressive refinement |

Instruction-conditioned training is especially important in the foundation-model era because it shifts audio editing from predefined task execution toward open-ended user intent following.

---

## Training-free Audio Editing

Training-free approaches adapt pretrained audio generative models to editing without parameter updates. They operate by manipulating inference-time mechanisms, such as inversion, attention control, prompt or guidance adjustment, and mask-based constraints.

| Paradigm | Description | Representative Scope |
|---|---|---|
| Inversion-Based Editing | Maps source audio back into the latent, noise, or trajectory space of a pretrained generative model, then edits it by modifying conditions or sampling trajectories. | DDPM/DDIM inversion, latent inversion, flow-based inversion, speech or music reconstruction and editing |
| Attention-Controlled Editing | Guides pretrained generative models by modifying or reusing internal attention patterns without parameter updates. | cross-attention event localization, self-attention preservation, prompt-level manipulation |
| Mask- and Region-Guided Editing | Specifies where to edit and where to preserve the source audio in waveform, spectrogram, latent, or source-component spaces. | localized editing, inpainting, restoration, source-level manipulation |
| Token-Level Editing with Codec Models | Manipulates discrete audio tokens through masking, infilling, continuation, or selective regeneration at inference time. | speech infilling, localized resynthesis, codec-token editing |

Training-free methods are flexible and data-efficient, but their performance remains sensitive to inversion accuracy, attention reliability, mask quality, temporal consistency, and non-target preservation.

---

## Resources

### Available Datasets

| Dataset | Domain | Typical Usage |
|---|---|---|
| LibriSpeech-Edit | Speech | localized text-based speech editing |
| Emilia / WenetSpeech4TTS | Speech | large-scale speech generation and editing backbone training |
| DailyTalk / SeniorTalk | Speech | dialogue-style speech editing and conversational speech modeling |
| AliMeeting / AMI | Speech | long-context and multi-speaker speech editing |
| Slakh2100 | Music | multi-track music editing with stems and MIDI annotations |
| MUSDB18 | Music | source separation, remixing, and instrument-level editing |
| MAESTRO | Music | score- and MIDI-conditioned music modeling |
| MusicCaps / MTG-Jamendo | Music | caption-, tag-, genre-, mood-, and instrument-conditioned music editing |
| NSynth / GTSinger | Music | timbre, note-level, lyrics, melody, and singing voice editing |
| AudioSet / FSD50K / ESC-50 | General Audio | sound-event modeling and event-level validation |
| AudioCaps / Clotho / WavCaps / AudioSetCaps | General Audio | audio-language grounding and caption-based supervision |
| VoiceBank+DEMAND / WHAM! / WHAMR! / DNS Challenge | General Audio | denoising, restoration, noisy mixtures, and reverberant mixtures |

### Data Tools

Given the scarcity of complete instruction-based editing datasets, data construction tools are essential for converting raw audio into structured and reusable editing supervision.

| Tool Type | Function | Examples of Produced Supervision |
|---|---|---|
| Temporal Localization Tools | Determine where an edit should be applied. | phone/word boundaries, speaker-active segments, event boundaries, pitch and note-level cues |
| Semantic Annotation Tools | Assign interpretable descriptions or labels to editable regions. | transcripts, captions, tags, sound-event labels, emotion labels |
| Pair Construction Tools | Create input-output pairs or instruction-input-output triplets. | TTS-based speech pairs, voice conversion pairs, degradation-restoration pairs, separation/remixing pairs |

### Evaluation Protocols and Benchmarks

Audio editing evaluation must assess not only output quality, but also edit success and preservation of non-target regions. Existing protocols can be summarized along four dimensions:

| Dimension | Question | Example Metrics |
|---|---|---|
| Edit Success and Instruction Adherence | Does the output correctly satisfy the requested edit? | human judgment, ASR-WER/CER, emotion2vec, CLAP similarity, tag accuracy, pitch or rhythm accuracy |
| Preservation and Locality | Are regions or attributes irrelevant to the edit preserved? | speaker similarity, waveform/spectrogram/embedding similarity, PESQ, STOI, SI-SDR, preservation MOS |
| Temporal and Structural Consistency | Does the edited output remain coherent in time and preserve relevant structure? | boundary error, WDTW, melody accuracy, Rhythm F1, dynamics correlation |
| Audio Quality and Naturalness | Does the edited audio sound realistic, continuous, and artifact-free? | MOS, CMOS, MOSNet, DNSMOS, NISQA, FAD, AuditScore, AuditEval |

Existing audio-language, audio-generation, and music-understanding benchmarks provide useful references, but a faithful benchmark specifically designed for audio editing should separately measure target modification, non-target preservation, temporal consistency, perceptual quality, and instruction following.

---

## Systemization Challenges and Future Directions

Foundation-model-based audio editing still faces several system-level challenges:

1. **Complex editing.**  
   Real-world recordings entangle semantic events, speaker identity, acoustic texture, background ambience, rhythm, spatial cues, and reverberation. Future systems should support object localization, attribute-level modification, and non-target preservation across speech, music, and general audio.

2. **Robustness under open-domain conditions.**  
   Editing models must remain stable when audio contains noise, reverberation, overlapping sources, long-range dependencies, or ambiguous user intents. Improving instruction grounding, long-context modeling, iterative refinement, self-verification, retrieval-augmented editing, and multi-stage correction are promising directions.

3. **Faithful and specific evaluation.**  
   Current protocols often conflate generation quality with editing quality. Reliable benchmarks should provide explicit annotations of target regions, edit operations, preservation regions, and control signals, enabling separate measurement of edit success and non-target preservation.

4. **Safety, copyright, and misuse prevention.**  
   Audio editing systems can realistically alter speech content, speaker identity, emotion, background sounds, and music. Watermarking, provenance tracking, edited-audio detection, and responsible data licensing are important for practical deployment.

---

## Citation

If you find this survey useful, please consider citing our paper.

```bibtex
@article{audioeditsurvey2026,
  title   = {Audio Editing in the Era of Foundation Models: A Survey},
  author  = {Anonymous Authors},
  journal = {arXiv preprint},
  year    = {2026}
}
```

---

## Contributing

We welcome issues and pull requests. If you find missing papers, datasets, benchmarks, or tools related to audio editing, please feel free to open an issue or submit a pull request.

## License

This repository is released for academic and research purposes. The license will be updated soon.
