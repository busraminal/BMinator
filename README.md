# 🧠 BMinator (DeepPersona)
**Word-Level Transformer-Based Personality-Driven Text & Story Generation System**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-yellow.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-Framework-red.svg)](https://pytorch.org/)
[![NLP](https://img.shields.io/badge/NLP-Generative_AI-green.svg)]()
[![Status: Prototype](https://img.shields.io/badge/Status-Prototype-orange.svg)]()


## 📖 Overview
**BMinator (DeepPersona)** is an AI system that creates **personalized digital characters and narrative texts** from a single face image.  
It combines **computer vision, word-level transformer models**, and **persona vectors** to produce stories that reflect the user’s personality.  
The project demonstrates how **AI can personalize content generation**, turning a simple image into a narrative infused with emotion, character, and individuality.

## 🎯 Project Purpose
> “From one face — a story, a soul, a synthetic persona.”

BMinator aims to:
- Analyze facial features via OpenCV & landmark detection.  
- Generate a **25-dimensional personality vector**.  
- Feed this vector into a **word-level transformer** to create unique story text.  
- Present the output as a coherent, personalized narrative.

## ⚙️ System Architecture
```
        [User Image Upload]
                  │
        ┌─────────▼─────────┐
        │ Face Analysis (OpenCV) │
        └─────────┬─────────┘
                  │ Persona Vector (25-dim)
        ┌─────────▼─────────┐
        │ Word-Level Transformer │
        └─────────┬─────────┘
                  │
        [Generated Personalized Story]
```

**Core Modules**
1. **Frontend:** (Planned) HTML/CSS + Flask interface for image upload & result display.  
2. **Backend:** Flask server running PyTorch models for face feature extraction & text generation.  
3. **Data Layer:** Word-level datasets; future versions will include SQL/PostgreSQL for storage.

---

## 🧩 Model Architecture & Training

| Component | Description |
|------------|-------------|
| **Input** | 25-dimensional persona vector + word token IDs |
| **Layers** | 4 Transformer blocks, 8-headed self-attention |
| **Embedding Size** | 128 |
| **Feed-Forward Dim** | 512 |
| **Dropout** | 0.20 |
| **Optimizer** | Adam (`lr=5e-4`) |
| **Loss** | CrossEntropy |
| **Dataset** | 20,000 word-level samples (split into 4 parts) |
| **Hardware** | NVIDIA A100 GPU (Google Colab) |

The model learns linguistic style conditioned on persona features — generating fluent, contextually coherent text in under **10 seconds** per sample.

---

## 🧠 Development Stages
| Stage | Approach | Result |
|--------|-----------|--------|
| **Phase 1:** Character-Level LSTM | Tried sequential char prediction | Poor long-range coherence |
| **Phase 2:** Word-Level LSTM | Switched to word embeddings | Better semantics & grammar |
| **Phase 3:** Transformer | Adopted word-level transformer | Stable, high-quality generation |

---

## 🧪 Evaluation & Testing
- **Semantic Test:** Manual review for narrative meaning and personality consistency.  
- **Loss Monitoring:** Smooth decline over 150 epochs.  
- **Speed Test:** 8–10 s/story on A100 GPU.  
- **Comparison:** Word-level Transformer ≫ char-level LSTM in fluency and contextuality.

---

## 💻 Technologies Used
| Category | Tools |
|-----------|-------|
| **Languages** | Python 3.10+ |
| **Frameworks** | PyTorch, NumPy, scikit-learn |
| **Vision** | OpenCV (face landmark detection) |
| **Visualization** | Matplotlib |
| **Training** | Google Colab (A100 GPU) |
| **IDE** | Visual Studio Code |
| **Planned UI** | Flask + HTML/CSS + Streamlit/Gradio |

---

## 📋 Functional Requirements
- Accepts one **face image** (`.jpg`, `.png`)  
- Extracts facial landmarks & derives persona vector  
- Generates personalized text within **<10 seconds**  
- Modular architecture for easy integration with TTS or avatar animation systems (e.g. SadTalker)

---

## 🧭 Non-Functional Requirements
- **Performance:** Fast inference under 10 s.  
- **Scalability:** Modular, extendable structure.  
- **Quality:** Grammatically consistent and semantically rich text.  

---

## 🧑‍💻 User Scenarios
| User Type | Use Case |
|------------|-----------|
| **Writer** | Auto-generate story ideas from random faces. |
| **Therapist** | Use AI avatars to build emotional connection. |
| **Creative Agency** | Prototype characters for media or advertising. |
| **Game Developer** | Import personalized backstories into games. |
| **Individual User** | Create a digital persona for emotional expression. |

---

## 🔮 Future Work
- Emotion-conditioned story generation.  
- Visual-based persona inference via CNN-Transformer hybrid.  
- Integration with Text-to-Speech (TTS) and avatar animation modules.  
- Streamlit / Gradio web interface for public demos.  

---

## 🧬 Example Usage
```bash
# Train
python train_word_transformer.py   --epochs 150   --batch_size 64   --save_dir checkpoints/

# Generate
python generate_word_level.py   --vector_file "sample.vec"   --model_checkpoint "checkpoints/model_150.pt"
```

_Output → `outputs/generated_text.txt`_

---

## 🧩 Dataset Structure
📁 data/  
 ├── word_vocab.json     # word-to-ID dictionary  
 ├── worddata_part1.json  
 ├── worddata_part2.json  
 ├── worddata_part3.json  
 └── worddata_part4.json  

---

## 🧠 Research & References
- Vaswani et al. (2017). *Attention Is All You Need.*  
- OpenCV Documentation (2024)  
- HuggingFace Transformers Library (2024)  
- SadTalker: *Single Image Talking Face Animation*  
- PyTorch Documentation (2024)  
- Google Colab, Matplotlib Docs  

---

## 👩‍💻 Author
**Büşra Mina Al**  
🎓 Ostim Technical University — AI & Industrial Engineering (Double Major)  
📧 busraminaa@gmail.com  
🧠 Specialization: NLP, Generative AI, Personality-Driven Models  

---

## ⚖️ License
Licensed under the **MIT License** — free for academic and commercial use.  
© 2025 Büşra Mina Al. All Rights Reserved.
