# 📄 Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition

This directory contains the dataset and related implementation details used in the following paper, including the prompt templates employed for rationale generation.

> Zhang M, Zhang Z, Wang Y, et al.  
> *Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition*  
> International Conference on Advanced Data Mining and Applications (ADMA), 2025.



## 🔍 Overview

This dataset is constructed for the task of **academic opinion recognition** in scientific literature.

- 📄 Source: ACL 2024 papers  
- 🎯 Task: Identify whether a sentence expresses an academic opinion  
- 🧠 Supervision: Each sentence is paired with a structured **rationale**

Rationales are generated using **GPT-4o** as the teacher model. Each rationale follows a structured **three-step reasoning template**:

- Step 1: Identify the key expression [trigger word/phrase] in the sentence.
- Step 2: Analyze that this expression [action verb] [object] and reflects [subjectivity type] (with brief explanation).
- Step 3: Therefore, the sentence matches [M code: mode name] and is classified as an opinion.
  

## ⚠️ Dataset Statistics

Due to an oversight, the statistics reported in the paper do not accurately reflect the final dataset, and **the statistics in the table below should be regarded as the authoritative reference**. The dataset contains **10,000 sentences** sampled from **ACL 2024 papers**.

| Label              | Train | Valid | Test | Total |
|-------------------|------:|------:|-----:|------:|
| Opinion (1)       | 3,779 | 490   | 482  | 4,751 |
| Non-opinion (0)   | 4,221 | 510   | 518  | 5,249 |
| **Total**         | 8,000 | 1,000 | 1,000 | 10,000 |


## 🧾 Data Format

Each instance is stored in **JSONL** format:

```json
{
  "text": "...",
  "label": 1,
  "rationale": "- Step 1: ...\n- Step 2: ...\n- Step 3: ..."
}
```

- `text`: input sentence  
- `label`: binary label (`1 = opinion`, `0 = non-opinion`)  
- `rationale`: structured explanation  


## 📌 Citation

If you find this dataset useful in your research, **please consider citing our paper**:

```bibtex
@inproceedings{zhang2025explain,
  title={Explain Before Classify: Contrastive Rationale Distillation for Academic Opinion Recognition},
  author={Zhang, M. and Zhang, Z. and Wang, Y. and others},
  booktitle={International Conference on Advanced Data Mining and Applications},
  pages={311--325},
  year={2025},
  organization={Springer Nature Singapore}
}
```
