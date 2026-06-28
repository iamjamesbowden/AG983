# AG983 — Class 1: Foundations of Text-as-Data and Representation

**University of Strathclyde Business School** | Dr James Bowden

This folder contains the workshop materials for Class 1, accompanying Section 6.4 of the lecture.

---

## Workshop: Text Pre-Processing — Decisions and Consequences

### Open the notebook in Google Colab

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/iamjamesbowden/AG983/blob/main/class1/AG983_Class1_Workshop.ipynb)

**Important:** when the notebook opens, go to **File → Save a copy in Drive** before doing anything else. Work from your own copy.

To run any cell: click on it and press **Shift+Enter**, or click the **▶ play button** to the left of the cell. Run cells in order from top to bottom.

---

## Materials

| File | Description |
|---|---|
| `AG983_Class1_Workshop.ipynb` | Google Colab notebook — work through this during the session |
| `AG983_Class1_Worksheet.md` | Worksheet — download, open in Word, answer questions as you go |
| `data/enron_sample.csv` | Enron email corpus (1,000 emails, 2000–2002) |

---

## The Corpus

The workshop uses a corpus drawn from the Enron email dataset (Klimt & Yang, 2004), released into the public domain by the Federal Energy Regulatory Commission during the 2001 investigation.

**1,000 emails** spanning three periods:

| Period | Dates | Description |
|---|---|---|
| `pre_crisis` | 2000 | Enron at peak — record revenues, Fortune Most Innovative Company |
| `crisis` | 2001 | Accounting irregularities emerge; share price collapses from $90 to under $1 |
| `collapse` | Late 2001–2002 | Bankruptcy filing; regulatory investigations; employee savings wiped out |

Five categories: `executive`, `trading`, `risk`, `operations`, `all_staff`

---

## Dictionaries

Two sentiment dictionaries are loaded automatically in Step 0 from the AG952 repository:

- **Loughran-McDonald (2011)** — 2,966 words; designed for financial and corporate disclosure text
- **Harvard General Inquirer** — 380 words; general-purpose; included for comparison

---

## Key References

Klimt, B. and Yang, Y. (2004) 'The Enron Corpus', *Machine Learning: ECML 2004*, pp. 217–226.

Loughran, T. and McDonald, B. (2011) 'When is a Liability not a Liability?', *Journal of Finance*, 66(1), pp. 35–65.

Renault, T. (2020) 'Sentiment analysis and machine learning in finance', *Digital Finance*, 2(1), pp. 1–13.

Todd, A., Bowden, J. and Moshfeghi, Y. (2024) 'Text-based sentiment analysis in finance', *Intelligent Systems in Accounting, Finance and Management*, 31.
