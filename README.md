**GITHUB REPO LINK**: https://github.com/lukecn03/COS760-Project-Group23
**The complete project files can be accessed via this Google Drive link**: https://drive.google.com/drive/folders/1SUBRad1jdldMOtAhwUnTnyl-kCAS5aU7?usp=sharing 

# COS760-Project-Group23
# Sentiment Analysis Using AfriSenti Datasets


**Luke Nobrega (u22517244) | Kudzai Nyika (u22585185) | Keabetswe Seitei (u26846404)**

---

## Project Overview

This project compares two multilingual transformer models, XLM-R and AfriBERTa on sentiment classification for Hausa and Kinyarwanda using the AfriSenti dataset. LIME and SHAP are applied to disagreement cases to explain why performance differences exist between the two models.

---

## Research Question

To what extent do models pretrained on high-resource languages (XLM-R) and African languages (AfriBERTa) differ in sentiment classification performance on African languages, and what do LIME and SHAP reveal about the linguistic reasons behind those differences?

---

## Dataset

- **Source:** AfriSenti - https://huggingface.co/datasets/masakhane/afrisenti
- **Languages:** Hausa (hau), Kinyarwanda (kin)
- **Task:** Three-class sentiment classification - positive, negative, neutral
- **Hausa training samples:** 14,172
- **Kinyarwanda training samples:** 3,302
- The data is downloaded automatically when you run `01_Data_Ingestion_and_Setup.ipynb`
- Do not include the data folder in the zip file — it is too large and will be downloaded fresh by the notebook
- Once downloaded, the notebook saves the processed files to your Google Drive under `Cos760/data/processed/
---
## Contents of the Zip File

| File | Description |
|------|-------------|
| README.md | Project overview, setup instructions, and how to run |
| 01_Data_Ingestion_and_Setup.ipynb | Downloads AfriSenti data, cleans tweets, saves processed CSVs to Drive |
| 02_Model_Training.ipynb | Fine-tunes XLM-R and AfriBERTa on Hausa and Kinyarwanda |
| 03_Evaluation.ipynb | Generates predictions, computes metrics, extracts disagreement cases |
| 04_Analysis.ipynb | Applies LIME and SHAP to disagreement cases, saves XAI outputs |
| 05_Reporting.ipynb | Compiles all results into final charts and tables |


---

## Models

| Model | HuggingFace ID | Description |
|-------|----------------|-------------|
| XLM-R | xlm-roberta-base | General purpose multilingual model |
| AfriBERTa | castorini/afriberta_large | Pretrained on 11 African languages |

---

## Results

| Language | Model | F1 (Weighted) | Accuracy |
|----------|-------|---------------|----------|
| Hausa | XLM-R | 0.7411 | 0.7407 |
| Hausa | AfriBERTa | 0.7942 | 0.7950 |
| Kinyarwanda | XLM-R | 0.5661 | 0.5750 |
| Kinyarwanda | AfriBERTa | 0.6193 | 0.6199 |

---

## How to Run

All notebooks are designed to run on Google Colab with a T4 GPU. The project files are stored on a shared Google Drive and are hardcoded to save and read files to and from a shared folder, link to folder at top of file.

**Step 1 : Mount Drive and set up data**
Open `01_Data_Ingestion_and_Setup.ipynb` and run all cells.

**Step 2 : Fine-tune both models**
Open `02_Model_Training.ipynb` and run all cells.

**Step 3 : Evaluate**
Open `03_Evaluation.ipynb` and run all cells.

**Step 4 : Analysis and XAI**
Open `04_Analysis.ipynb` and run all cells.

**Step 5 : Reporting**
Open `05_Reporting.ipynb` and run all cells.

---

## Requirements

All dependencies are installed at the top of each notebook. Key libraries:

- transformers
- torch
- datasets
- scikit-learn
- lime
- shap
- matplotlib
- seaborn
- pandas

---

## Key Findings

- AfriBERTa outperforms XLM-R on both languages
- XLM-R over-relies on culturally loaded tokens like *allah* in ways that do not generalise to African language contexts
- AfriBERTa correctly identifies language-specific vocabulary like *gukunda* (to love in Kinyarwanda) as sentiment signals
- Africa-centric pretraining produces more contextually grounded feature weighting for African language sentiment analysis

---
