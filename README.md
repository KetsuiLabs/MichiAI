<p align="center">
  <img src="https://cdn.prod.website-files.com/67127eed69ff4a051cdcecf3/69428a0a5e10b3238596cf9c_a14f635e2e0835454d6e9d3f54bb56a4_MichiLogo.jpg" width="600" alt="Architecture Diagram">

<div align="center">
  <p><b>A full-duplex speech LLM with ~75ms latency.</b></p>
</div>
</p>


**MichiAI** is a lightweight, multimodal speech large language model designed for **full-duplex interaction**. \
Unlike traditional serial pipelines (ASR → LLM → TTS), MichiAI can listen and speak simultaneously, mimicking natural human conversation with ultra-low latency.


[![Read the Blog Post](https://img.shields.io/badge/Read_the_Blog_Post-MichiAI_Part_1-ff7200?style=for-the-badge&logo=ghost)](https://ketsuilabs.io/blog/introducing-michi-ai)

## ⚡ Quick Specs

| Feature | Specification |
| :--- | :--- |
| **Model Size** | 530M Parameters |
| **Latency (TTFA)** | ~75ms (tested on RTX 4090) |
| **Architecture** | Continuous Embeddings + Rectified Flow Matching |
| **Base Backbone** | SmolLM-360m |
| **Key Innovation** | No Coherence Loss / Single Step Decoding |


## 🌟 Key Features

* **Full-Duplex Capability:** Handles interjections and backchanneling implicitly. It "hears" while it "talks."
* **Continuous Audio Latents:** Bypasses the slow decoding of traditional RVQ (Residual Vector Quantization) models. This enables **high-fidelity audio** with much fewer forward passes.
* **Zero-Shot Voice Cloning:** Captures vocal timbre and style from just a few seconds of audio prompt.
* **Multimodal Input:** Supports mixed text and audio prompting, making it compatible with existing RAG (Retrieval-Augmented Generation) frameworks.
* **No Coherence Loss:** Retains the reasoning and linguistic capabilities of the underlying text LLM without the typical degradation seen in speech-to-speech models.
* **Paralinguistics:** Naturally models breathing, laughing, and emotional prosody learned directly from the dataset.


## 🤖 Architecture Overview

### 1. The Listening Head
A multi-modal encoder mapping raw audio into continuous embeddings while simultaneously generating text tokens. This ensures the model understands both the semantic meaning and the emotional context.

### 2. The Speaking Head
Predicts audio embeddings using **Rectified Flow Matching**. This allows for fast, high-quality, and diverse speech generation. The embeddings are then processed through a lightweight, causal **HiFi-GAN vocoder** for real-time streaming.


## 📊 Performance Comparison

Despite being significantly smaller and trained on less data, MichiAI maintains high reasoning capabilities by efficiently utilizing pretrained text knowledge.

| Model | Parameters | Audio Training Data | Approach |
| :--- | :--- | :--- | :--- |
| Hertz-dev | 8.5B | 20,000,000 hours | Quantized |
| Moshi | 7B | 7,000,000 hours | Quantized |
| Qwen-Omni | 7B+ | 8,000,000+ hours | Quantized |
| **MichiAI** | **530M** | **~5,000 hours** | **Continuous** |


## 🚀 Roadmap

* [x] **Core Architecture:** Continuous Embeddings + Flow Matching implementation.
* [ ] **Scaling:** Implementing a larger LLM backbone.
* [ ] **Conversational Tuning:** Training on specific dialogue datasets for better turn-taking.
* [ ] **Multilingual Support:** Integrating non-English datasets.
* [ ] **Hugging Face Space:** Launching a live interactive demo.
* [ ] **Release API client** Release an API client to this repo
