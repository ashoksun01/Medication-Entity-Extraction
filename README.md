# Medication-Entity-Extraction

# Medication Entity Extraction Using Transformer Models and Mistral-7B

## Project Summary
This project focuses on extracting medication-related entities from clinical texts using Named Entity Recognition (NER) with transformer models. We compare the performance of BERT-based models (BERT-base-cased, BiomedBERT, Clinical-Longformer) with the Mistral-7B large language model (LLM). Our primary goal is to identify medication entities such as Drug, Dosage, Form, Frequency, Route, Strength, Reason, Duration, and Adverse Drug Events (ADEs) within electronic health records (EHRs).

- **Problem:** Extracting clinically relevant medication information from unstructured EHRs is challenging due to data complexity, inconsistent terminology, and variability in text quality.
- **Solution:** We leverage transformer-based models and Mistral-7B to accurately extract key medication entities, supporting safer and more efficient clinical decision-making.
- **Target Users:** Healthcare providers, clinical researchers, and organizations seeking to enhance medication safety through automated text processing.

---

## Repository Structure

---

## How It Works
1. **Data Source:** Our dataset is the "2018 n2c2 Adverse Drug Events and Medication Extraction Dataset" obtained through Harvard Medical School's DBMI Portal.
2. **Data Preprocessing:** 
   - For transformer models, data is preprocessed using the BIO (Beginning, Inside, Outside) tagging scheme.
   - For Mistral-7B, data is transformed into JSON format for compatibility with the LLM.
3. **Modeling Techniques:**
   - We fine-tune three transformer models:
     - **BERT-base-cased:** A general transformer model for NER tasks.
     - **BiomedBERT:** A domain-specific transformer pre-trained on biomedical texts.
     - **Clinical-Longformer:** A long-text transformer optimized for clinical documents.
   - We also experiment with Mistral-7B:
     - Few-shot, zero-shot, and fine-tuned setups are tested.
4. **Entity Extraction:** The models extract the following entities:
   - Drug, Dosage, Form, Frequency, Route, Strength, Reason, Duration, and Adverse Drug Events (ADEs).
5. **Evaluation:** Model performance is evaluated using Precision, Recall, and F1 Score.

---

## Data Source
- **Dataset:** 2018 n2c2 Adverse Drug Events and Medication Extraction Dataset (Harvard Medical School DBMI Portal).
- **Entities Extracted:**
  - Drug, Dosage, Form, Frequency, Route, Strength, Reason, Duration, and ADE (Adverse Drug Events).
- **Data Format:**
  - For transformer models: BIO-tagged text (Beginning, Inside, Outside).
  - For Mistral-7B: JSONL format with structured entities.

---

## Model Performance
### Transformer Models (BERT, BiomedBERT, Clinical-Longformer)
| Model                | Precision | Recall | F1 Score |
|-----------------------|------------|---------|-----------|
| BERT-base-cased        | 0.84       | 0.88    | 0.86      |
| Microsoft BiomedBERT   | 0.89       | 0.86    | 0.88      |
| Clinical-Longformer    | 0.87       | 0.86    | 0.87      |

| Entity   | BERT-base-cased (Precision / Recall / F1) | Microsoft BBB (Precision / Recall / F1) | Clinical-Longformer (Precision / Recall / F1) |
|-----------|--------------------------------------------|-------------------------------------------|------------------------------------------------|
| ADE       | 0.45 / 0.39 / 0.42                         | 0.43 / 0.53 / 0.48                        | 0.54 / 0.54 / 0.54                             |
| Dosage    | 0.87 / 0.91 / 0.89                         | 0.89 / 0.93 / 0.91                        | 0.89 / 0.88 / 0.89                             |
| Drug      | 0.88 / 0.94 / 0.91                         | 0.91 / 0.94 / 0.92                        | 0.93 / 0.91 / 0.92                             |
| Duration  | 0.55 / 0.68 / 0.61                         | 0.62 / 0.74 / 0.68                        | 0.67 / 0.68 / 0.68                             |
| Form      | 0.94 / 0.91 / 0.92                         | 0.93 / 0.92 / 0.92                        | 0.92 / 0.91 / 0.91                             |
| Frequency | 0.78 / 0.82 / 0.80                         | 0.83 / 0.85 / 0.84                        | 0.80 / 0.81 / 0.80                             |
| Reason    | 0.47 / 0.64 / 0.54                         | 0.54 / 0.66 / 0.59                        | 0.62 / 0.58 / 0.60                             |
| Route     | 0.94 / 0.94 / 0.94                         | 0.93 / 0.93 / 0.93                        | 0.93 / 0.92 / 0.92                             |
| Strength  | 0.94 / 0.96 / 0.95                         | 0.95 / 0.96 / 0.95                        | 0.93 / 0.94 / 0.93                             |

### Mistral-7B Performance (Zero-Shot, Fine-Tuned)
| Model                  | Precision | Recall | F1 Score (Full) | F1 Score (Non-Empty) |
|-------------------------|------------|---------|-------------------|-----------------------|
| Mistral-7B Few-Shot      | 0.17       | 0.18    | 0.15               | 0.41                  |
| Mistral-7B Zero-Shot     | 0.44       | 0.47    | 0.41               | 0.66                  |
| Mistral-7B Few-Shot FT   | 0.36       | 0.37    | 0.34               | 0.45                  |

---

## Key Learnings & Impact
- **Text Complexity:** Clinical text is highly unstructured, making NER challenging.
- **Class Imbalance:** Focal loss improved detection of rare entities like ADE.
- **LLM Limitations:** Mistral-7B's performance was lower than BERT-based models for NER due to difficulty with precision in entity extraction.
- **Optimized Transformer Models:** BiomedBERT and Clinical-Longformer outperformed Mistral-7B in ADE detection.

---

## Future Improvements
- **Enhanced Data Augmentation:** Explore more sophisticated text augmentation methods.
- **Advanced Fine-Tuning:** Refine Mistral-7B using domain-specific prompts and larger datasets.
- **Model Ensemble:** Experiment with model ensembling to leverage strengths of multiple models.
- **User Interface:** Develop an interactive web application for NER-based EHR processing.

---
