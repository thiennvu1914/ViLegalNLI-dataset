# 🇻🇳 ViLegalNLI: Vietnamese Legal Natural Language Inference Dataset

**Course project:** Natural Language Processing for Data Science  
**Institution:** University of Information Technology — VNU-HCM

ViLegalNLI is a Vietnamese legal-domain Natural Language Inference (NLI) dataset developed to support research on entailment, neutrality, and contradiction in low-resource, domain-specific language understanding.

## Dataset Summary

| Property | Value |
|---|---:|
| Premise–hypothesis pairs | 9,696 |
| Source legal documents | 3,232 |
| Legal aspects | 26 |
| Labels | 3 |
| Entailment examples | 3,232 |
| Neutral examples | 3,232 |
| Contradiction examples | 3,232 |
| Source websites | 3 |
| File format | XLSX |

The workbook currently contains one sheet named `Sheet1`. It does not provide an official train/dev/test split.

## Label Mapping

| Label | Meaning |
|---:|---|
| `0` | Entailment |
| `1` | Neutral |
| `2` | Contradiction |

## Schema

| Column | Description |
|---|---|
| `Hypothesis` | Statement whose relation to the premise is classified |
| `Premise` | Relevant legal passage used for NLI |
| `Text` | Longer source document context |
| `Aspect` | Legal-domain category |
| `Website` | Source website |
| `Label` | Integer NLI label |
| `List Evidence` | Evidence supporting the assigned relation, when applicable |
| `Explanation` | Natural-language explanation of the label |
| `File Path` | Historical collection path; not a portable identifier |
| `Text Length` | Recorded source-text length |

## Source Distribution

- `thuvienphapluat.vn`: 5,802 examples
- `vanban.chinhphu.vn`: 2,400 examples
- `dulieuphapluat.vn`: 1,494 examples

The dataset covers 26 aspects. The largest categories include public administration, other legal topics, public finance, investment, transportation, education, civil law, and construction/urban development.

## Load the Dataset

```python
import pandas as pd

df = pd.read_excel("dataset/ViLegalNLI.xlsx")
print(df.shape)            # (9696, 10)
print(df["Label"].value_counts().sort_index())
```

Install the required reader with:

```bash
pip install pandas openpyxl
```

## Data Quality Notes

A direct audit of the published workbook found:

- 13 rows with a missing `Hypothesis`
- 24 rows with a missing `Premise`
- 13 duplicated premise–hypothesis pairs
- no fully duplicated rows
- balanced label counts

Users should define and document how these rows are handled. When creating data splits, group related examples by their source document to reduce leakage between training and evaluation sets.

## Intended Use and Limitations

ViLegalNLI is intended for academic research and model evaluation in Vietnamese legal NLP. It is not legal advice and should not be used as the sole basis for legal decisions.

Legal language changes over time, source websites may contain copyrighted material, and automatically generated hypotheses or explanations may contain errors. Researchers should review source rights, dataset provenance, and applicable terms before redistribution or commercial use.

## Repository Structure

```text
ViLegalNLI-dataset/
├── dataset/
│   └── ViLegalNLI.xlsx
├── Source/
│   ├── BuildingViLegalNLI.ipynb
│   └── TrainingModel.ipynb
├── Report/
└── README.md
```

## Team

- Nguyen Phi Long
- Ho Nguyen Thien Vu
- Duong Thi Hong Nhung

**Instructor:** M.A. Huynh Van Tin

## References

This project was informed by SNLI, XNLI, ViNLI, ViHealthNLI, ViFactCheck, PhoBERT, XLM-R, CafeBERT, and mBERT.

- [PhoBERT paper](https://arxiv.org/abs/2003.00744)
- [XLM-R paper](https://arxiv.org/abs/1911.02116)

## License and Citation

No explicit dataset license has been published yet. Do not assume permission for redistribution or commercial use. For research-use questions or citation details, contact the repository maintainer through GitHub.

**Project completion:** 2024
