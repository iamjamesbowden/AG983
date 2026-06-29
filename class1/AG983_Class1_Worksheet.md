# AG983: Textual Analytics for Accounting and Finance
## Class 1 Workshop Worksheet — Text Pre-Processing: Decisions and Consequences

**Name:** _____________________________ &nbsp;&nbsp;&nbsp;&nbsp; **Date:** _____________________________

---

This worksheet accompanies the Class 1 Colab notebook. Complete each question as you work through the notebook, recording your observations, choices, and justifications. Submit as a Word document.

---

### Background: The Enron Corpus

The corpus used in this workshop is drawn from the Enron email dataset (Klimt & Yang, 2004), released into the public domain by the Federal Energy Regulatory Commission (FERC) during the 2001 investigation into Enron Corporation.

The corpus spans three periods:
- **Pre-crisis (2000):** Enron at peak — named Fortune's Most Innovative Company for the fifth consecutive year; record revenues
- **Crisis (2001):** Accounting irregularities emerge; Sherron Watkins writes her whistleblower memo; share price collapses from $90 to under $1
- **Collapse (late 2001–2002):** Chapter 11 bankruptcy filing; regulatory investigations; employee retirement savings wiped out

This corpus is particularly useful for preprocessing exercises because it combines the *hedged, forward-looking register of corporate financial communication* with the *informal directness of internal correspondence* — precisely the combination that exposes the limitations of generic NLP pipelines.

---

## Section A: Corpus Exploration (Step 1)

**Question 1.** After running Step 1 in the notebook, answer the following:

a) How many emails are in the corpus, and how are they distributed across the three time periods?

&nbsp;

&nbsp;

b) What is the mean email length in words? What is the range (shortest to longest)? What does this variation in length tell you about the register diversity of the corpus?

&nbsp;

&nbsp;

c) Look at the raw email printed in the notebook. Identify at least **three preprocessing challenges** visible in the raw text (e.g. punctuation attached to words, mixed case, numbers embedded in text).

| # | Preprocessing challenge | Example from the text |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

---

## Section B: Tokenisation (Step 2)

**Question 2.**

a) How many tokens does NLTK's `word_tokenize` produce compared to whitespace splitting for the sample email? Which is larger and why?

&nbsp;

b) The Loughran-McDonald dictionary contains the entry `losses`. If a document contains the string `"losses."` (with a full stop attached), will a whitespace tokeniser match it against the dictionary? Explain why or why not.

&nbsp;

&nbsp;

c) Why does this matter for the reliability of a sentiment score computed from corporate disclosure text?

&nbsp;

&nbsp;

---

## Section C: Case Folding and Punctuation Removal (Step 3)

**Question 3.**

a) Compare the four frequency distribution charts. What is the most obvious change between "NLTK tokenise only" and "Case-fold + punct removed"?

&nbsp;

b) The notebook quotes Renault (2020): retaining `!` and `?` improves financial sentiment classification by 0.3%. For a corpus of corporate email like Enron, would you retain or remove these characters? Justify your answer with reference to the type of text you are analysing.

&nbsp;

&nbsp;

c) The Enron corpus contains emails with phrases like `"EBITDA margins improved"`. What happens to the token `EBITDA` after case folding? Is this a potential problem for dictionary-based sentiment analysis?

&nbsp;

&nbsp;

---

## Section D: Stop-Word Removal (Step 4)

**Question 4.** This is one of the most consequential decisions in preprocessing financial text.

a) The Step 0 output shows which finance-significant terms are present in NLTK's standard stop-word list. List three of them here:

| Term | Analytical role in financial text |
|---|---|
| | |
| | |
| | |

b) In your own words, explain why removing these terms from a corporate email corpus would damage a sentiment analysis.

&nbsp;

&nbsp;

c) For each of the following terms, give an example sentence from financial text where removing it would distort meaning or sentiment:

| Term | Example sentence | Effect of removing it |
|---|---|---|
| `not` | | |
| `will` | | |
| `down` | | |

d) Which stop-word setting did you choose? Justify your choice with reference to the lecture material and the specific nature of the Enron corpus.

**My choice:** ☐ None &nbsp; ☐ Standard NLTK &nbsp; ☐ Finance-adjusted

**Justification:**

&nbsp;

&nbsp;

---

## Section E: Normalisation — Stemming vs Lemmatisation (Steps 5–6)

**Question 5.**

a) The notebook comparison table shows that Porter stemming produces `declin` from `declining`. The Loughran-McDonald dictionary contains `decline` but not `declin`. What is the consequence for your sentiment score?

&nbsp;

b) Find one example in the Step 6 table where lemmatisation preserves an LM dictionary match that stemming would destroy. Record it here:

| Token | Porter stem | Lemma | LM match: raw | LM match: stem | LM match: lemma |
|---|---|---|---|---|---|
| | | | | | |

c) The lecture notes that stemming may be defensible "when lemmatisation is computationally infeasible." Given that the Enron corpus has 1,000 emails, is computational cost a meaningful constraint? What would your answer be for a corpus of one million SEC filings?

&nbsp;

&nbsp;

d) Which normalisation method did you choose? Justify your choice.

**My choice:** ☐ None &nbsp; ☐ Porter Stemming &nbsp; ☐ Lemmatisation

**Justification:**

&nbsp;

&nbsp;

---

## Section F: The Pipeline Diagnostic (Step 7)

**Question 6.**

a) Record your pipeline's LM match counts and compare to the misconfigured pipeline:

| | Your pipeline | Misconfigured pipeline |
|---|---|---|
| LM Positive matches | | |
| LM Negative matches | | |
| Total LM matches | | |

b) By what percentage does your pipeline outperform the misconfigured version? What specific pipeline decisions account for this improvement?

&nbsp;

&nbsp;

c) The net sentiment chart shows LM sentiment across the three Enron periods. Describe the pattern. Does the direction of change match what you would expect given Enron's history? Explain any surprises.

&nbsp;

&nbsp;

d) Renault (2020) concludes that "algorithm choice explains far less variance than pipeline quality." Based on what you have observed in this exercise, do you find this claim plausible? Explain in 2–3 sentences.

&nbsp;

&nbsp;

---

## Section G: Dictionary Comparison (Step 9)

**Question 7.** Loughran & McDonald (2011) demonstrate that between 73% and 80% of negative words identified by the Harvard General Inquirer are not negative in a financial context.

a) The notebook shows tokens flagged negative by Harvard GI but not by LM. List three such tokens and explain why they would be incorrectly labelled negative in a financial document:

| Token | Why not negative in a financial context |
|---|---|
| | |
| | |
| | |

b) List three tokens flagged negative by LM but not by Harvard GI. Explain why they carry negative meaning in corporate disclosure:

| Token | Why negative in a financial disclosure context |
|---|---|
| | |
| | |
| | |

c) Which dictionary would you use for a study of corporate sentiment in SEC filings? Justify your choice.

&nbsp;

&nbsp;

---

## Section H: Corpus Bias (Step 10)

**Question 8.** Apply the six bias types from Section 6.5 of the lecture to the Enron corpus:

| Bias type | Applies? | Explain specifically how |
|---|---|---|
| **Resource** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Incentive** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Medium** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Retrieval** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Survivorship** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Self-reporting** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |

**Question 9.** The Step 10 chart shows net LM sentiment broken down by category and period. Does the executive category show the pattern you would predict under incentive bias — specifically, that executives would use more positive language than the underlying financial condition warrants? Comment on what you observe.

&nbsp;

&nbsp;

---

## Section I: Your Final Pipeline

**Question 10.** Record your final pipeline settings and justify each choice with reference to the lecture and/or the literature.

| Decision | Your choice | Academic justification (cite a source where possible) |
|---|---|---|
| Tokenisation | NLTK `word_tokenize` | |
| Case folding | ☐ Yes &nbsp; ☐ No | |
| Punctuation removal | ☐ Yes &nbsp; ☐ No | |
| Stop-word list | | |
| Number handling | | |
| Normalisation | | |
| Min document frequency | | |
| Max document frequency | | |

**Question 11.** In no more than 150 words, write a methods paragraph suitable for a research paper describing your pre-processing pipeline. Justify each decision with reference to relevant literature, following the conventions of academic writing.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

## References

Grimmer, J., Roberts, M.E. and Stewart, B.M. (2022) *Text as Data: A New Framework for Machine Learning and the Social Sciences*. Princeton: Princeton University Press.

Klimt, B. and Yang, Y. (2004) 'The Enron Corpus: A New Dataset for Email Classification Research', *Machine Learning: ECML 2004*, pp. 217–226.

Loughran, T. and McDonald, B. (2011) 'When is a Liability not a Liability? Textual Analysis, Dictionaries, and 10-Ks', *Journal of Finance*, 66(1), pp. 35–65.

Porter, M.F. (1980) 'An algorithm for suffix stripping', *Program*, 14(3), pp. 130–137.

Renault, T. (2020) 'Sentiment analysis and machine learning in finance: a comparison of methods and models on one million messages', *Digital Finance*, 2(1), pp. 1–13.

Todd, A., Bowden, J. and Moshfeghi, Y. (2024) 'Text-based sentiment analysis in finance: synthesising the existing literature and exploring future directions', *Intelligent Systems in Accounting, Finance and Management*, 31.
