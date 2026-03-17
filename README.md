# VDR-Bench & VDAT Framework

Welcome to the official repository for **VDR-Bench** (Video Dynamics Reasoning Benchmark) and the **VDAT** (Video Dynamics Analysis Tree) inference framework. This repository provides code and data to evaluate and mitigate logical hallucinations in Large Vision-Language Models (LVLMs) for video dynamics reasoning.

## 📊 Dataset: VDR-Bench

**VDR-Bench** is a comprehensive dataset designed to evaluate the spatio-temporal video comprehension of LVLMs.

- **Dataset Link:** [Hugging Face - VDR-Bench](https://huggingface.co/datasets/m3a4nyou5/mm-veu)
- **Size:** 2,700 curated videos and 5,400 high-quality question-answer pairs.
- **Format:** JSON Lines (`.jsonl`) format for maximum interoperability.

### Data Categorization
The dataset is systematically categorized along two primary axes:
1. **Temporal Dimension:** Sequence, Reasoning, Prediction, Pacing, and Change.
2. **Video Duration:** Short, Medium, and Long.

### Schema
Each JSON object in the dataset strictly encapsulates the following multi-modal evaluation metadata:
- Primary evaluation question
- Multiple-choice options
- Verifiable ground-truth answers
- A structurally linked logical sub-question (A, B, C) designed to detect hallucinations
- Detailed video captions

### Source Corpora
The videos are sourced from public benchmarks including **Video-MME** and **Google-DeepMind**, supplemented by clips from YouTube (e.g., *Friends TV show*, *SpongeBob SquarePants*, and *TED talks*) to cover diverse, open-domain dynamic scenarios.

### Data Curation Pipeline
We applied a rigorous three-stage pipeline to construct the dataset:
1. **Expert Annotation:** Initial expert annotations on 500 sets to map temporal logic to visual cues.
2. **Systematic Scaling:** Scaled via GPT-4o using base64 frame sampling and strict template guidance.
3. **Quality Review:** A human-in-the-loop review to filter out questions with "information leakage", stereotypical biases, or text-only solvability, ensuring true spatio-temporal video comprehension is required.

---

## 💻 Codebase Operations

This repository contains the custom codebase and infrastructure supporting the **Video Dynamics Analysis Tree (VDAT)** inference framework and our hallucination-mitigation methodology.

### 1. Evaluation Pipeline (`/eval/`)
Contains algorithms to execute VDAT, assess multi-dimensional reasoning accuracy, and track logical hallucinations.
- **Key Scripts:** `cal_ac.py`, `llava_eval.py`, `score.py`
- Handles automated inference, prediction logging, and the calculation of our proposed **Logical Hallucination Index (LHI)**.
- **Supported Models:** Integrated testing scripts for frontier models including *VideoLLaMA-3*, *Qwen2.5-VL*, *VILA1.5*, and *LLaVA-OneVision*.

### 2. Model Fine-Tuning (`/finetune/`)
Includes scripts to replicate the Quantized Low-Rank Adaptation (QLoRA) and Supervised Fine-Tuning (SFT) pipeline.
- Ensures models can be trained to improve semantic consistency as tested in the study.

---

## 📄 Licenses

To ensure maximum reproducibility, transparency, and reusability:
- **Dataset:** The annotated data and VDR-Bench schemas are released under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.
- **Code:** All source code in this repository is provided under the MIT/Apache 2.0 open-source license.

## 🔗 Links
- **Primary Repository:** [https://github.com/m4an5you6/VDR-Bench](https://github.com/m4an5you6/VDR-Bench)
- **Dataset:** [Hugging Face](https://huggingface.co/datasets/m3a4nyou5/mm-veu)
