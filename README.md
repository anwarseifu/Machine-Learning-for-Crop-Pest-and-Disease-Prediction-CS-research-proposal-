# 🌿 ML for Crop Pest & Disease Prediction



---

## Abstract

Agriculture feeds the world, but pests and diseases silently destroy 20–40% of global crops every year. The biggest frustration? Most of that loss is preventable — if we catch the problem early enough. This research proposes a Machine Learning system that fuses drone camera imagery with IoT environmental sensor data to detect and predict crop pest outbreaks before they cause serious damage. By combining visual and environmental signals in a Hybrid CNN-Transformer model, the goal is to give farmers in Ethiopia and beyond a practical, affordable early-warning tool that works in real field conditions — not just in a clean lab.

---

## The Problem

In a perfect world, a farmer would know about a pest outbreak days before it happens and treat just the affected area with minimal chemicals. The reality in Ethiopia looks very different. Most farmers still walk through miles of crops inspecting plants by hand. By the time a brown spot or a bug infestation is visible to the human eye, the disease has already spread. The response is usually heavy pesticide spraying across the whole field — expensive, harmful to the environment, and often not enough to save the crop. This research exists because that cycle doesn't have to continue.

---

## The Approach

The system is designed as a **Multi-Modal Fusion Pipeline** — meaning the AI processes two different types of data at the same time rather than relying on images alone.

- 📷 **Visual Input** — Drone cameras capture leaf and crop images which are standardized to 224×224 pixels and augmented with blur and noise to simulate real field conditions.
- 🌡️ **Environmental Input** — IoT sensors collect temperature and humidity readings, which are normalized using Z-score scaling so they can be compared on the same scale as image features.

Both streams are merged in a **Late-Fusion Layer**, where the model learns that context matters. A brown spot in dry, cool weather is very different from the same spot when humidity is high and temperatures have been climbing for days. This combined understanding is what makes the prediction smarter.

---

## Research Goals

**1. High-Precision Disease Classification**
Train a Hybrid CNN-Transformer model to identify 15 distinct pest and disease categories from the PlantVillage dataset, targeting an F1-score of at least **0.90**. Macro-averaging is used so rare diseases are treated with the same importance as common ones.

**2. Environmental Risk Modeling**
Analyze how temperature and humidity patterns correlate with disease spread rates, and use that data to generate a **Risk Probability Score** that forecasts the likelihood of an outbreak within a **48-hour window**.

**3. Real-World Robustness**
Ensure the model holds up under real drone conditions — blurry images, low resolution, poor lighting — maintaining at least **85% accuracy**. A lab-only model is not useful to a farmer.

---

## What the Literature Says

Five peer-reviewed papers from IEEE, ACM, and ScienceDirect (2022–2026) were reviewed, and three consistent gaps kept appearing across all of them:

- **Lab vs. Reality** — Models perform near-perfectly in controlled environments but accuracy drops significantly the moment they move to an actual field (Karthik et al., 2023; Das et al., 2025).
- **Computational Cost** — Processing high-resolution drone imagery demands more computing power than most field hardware can handle (Ahmad et al., 2024).
- **Disconnected Data** — Weather monitoring and visual detection are almost always studied in isolation. Nobody has properly combined them yet (Babu et al., 2024; Kumar et al., 2024).

This research directly addresses all three gaps.

---

## Tools & Technology

| Tool | Purpose |
|------|---------|
| **PyTorch** | Building and training the Hybrid CNN-Transformer model |
| **OpenCV** | Image preprocessing and augmentation |
| **Scikit-learn** | Baseline comparisons and feature scaling |
| **PlantVillage Dataset** | Primary training data (54,000+ labeled plant images) |
| **DLCPD-25** | Real-world field testing dataset |

PyTorch was chosen specifically because its dynamic computation graphs make multi-modal data fusion experiments significantly easier than static-graph alternatives.

---

## How Success Is Measured

- **Macro F1-Score** — Balances precision and recall across all 15 disease classes equally
- **Mean Absolute Error (MAE)** — Measures how accurate the 48-hour risk score predictions are against actual field observations
- **Inference Latency** — The full pipeline must complete in under **500ms per image** to support real-time drone deployment

---

## Project Timeline

| Phase | Weeks |
|-------|-------|
| Literature Review | 1–2 |
| Data Preparation | 3–4 |
| Model Training | 5–8 |
| Testing & Validation | 9–10 |
| Final Documentation | 11–12 |

---

## Ethics

Even though this project is about plants, it touches real people and real land. Three areas are taken seriously:

- **Privacy** — Farm GPS data will be anonymized following GDPR principles. No land ownership or personal identification data will be retained.
- **Fairness** — The model is trained on diverse crops, not just high-value commercial ones. Smallholder farmers deserve accurate predictions too.
- **Environmental Cost** — Transfer Learning is used instead of training from scratch, significantly reducing electricity consumption during model development.

---

## References

1. Karthik et al. (2023) — *ML for Plant Disease Detection*, IEEE Access
2. Ahmad et al. (2024) — *Precision Agriculture using UAV Imagery*, Drones Journal
3. Kumar et al. (2024) — *ML on Field Data for Agricultural Resilience*, ACM EAI
4. Das et al. (2025) — *Tea Leaf Disease Detection*, Scientific Reports
5. Babu et al. (2024) — *IoT-Enabled Crop Disease Prediction*, Lex Localis

---

## About

**Anwar Seifu** |  (ID: 1317/16)
| Instructor: Mr. Birhane Bekele | May 1, 2026
