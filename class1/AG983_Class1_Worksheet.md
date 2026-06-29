# AG983: Textual Analytics for Accounting and Finance
## Class 1 Workshop Worksheet

**Name:** _________________________ &nbsp;&nbsp;&nbsp;&nbsp; **Date:** _________________________

Complete each question as you work through the Colab notebook. Submit as a Word document.

---

### The Enron Corpus

The corpus used in this workshop is drawn from the Enron email dataset (Klimt & Yang, 2004), released into the public domain by the Federal Energy Regulatory Commission during the 2001 investigation into Enron Corporation. The corpus covers three periods:

- **Pre-crisis (2000):** Enron at peak performance, named Fortune's Most Innovative Company for the fifth consecutive year
- **Crisis (2001):** Accounting irregularities emerge; Sherron Watkins writes to Ken Lay; share price falls from $90 to under $1
- **Collapse (late 2001 to 2002):** Chapter 11 bankruptcy; regulatory investigations; employee retirement savings wiped out

The corpus was selected because it combines the hedged, forward-looking register of corporate financial disclosure with the informal directness of internal correspondence. That combination tests the limitations of generic preprocessing pipelines in ways that a standard newswire corpus would not.

---

## Section A: Corpus Exploration (Step 1)

**Question 1.**

a) How many emails are in the corpus? How are they distributed across the three time periods?

&nbsp;

&nbsp;

b) What is the mean email length? What is the range from shortest to longest? What does the variation in length suggest about the register diversity of the corpus?

&nbsp;

&nbsp;

c) Examine the raw email printed in the notebook. Identify at least three preprocessing challenges visible in the text before any cleaning is applied.

| # | Challenge | Example from the text |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

---

## Section B: Tokenisation (Step 2)

**Question 2.**

a) How many tokens does NLTK's `word_tokenize` produce compared with whitespace splitting for the sample email? Which produces more tokens and why?

&nbsp;

b) The Loughran-McDonald dictionary contains the entry `losses`. If a document contains the string `"losses."` with a full stop attached, will a whitespace tokeniser match it against the dictionary? Explain.

&nbsp;

&nbsp;

c) Why does the tokenisation method matter for the reliability of a sentiment score computed from corporate disclosure text?

&nbsp;

&nbsp;

---

## Section C: Case Folding and Punctuation Removal (Step 3)

**Question 3.**

a) Comparing the four frequency distribution panels, what is the most obvious change between "NLTK tokenise only" and "Case-fold + punct removed"?

&nbsp;

b) Renault (2020) finds that retaining `!` and `?` improves financial sentiment classification by 0.3%. For a corpus of corporate email, would you retain or remove these characters? Justify your answer with reference to the type of text you are analysing.

&nbsp;

&nbsp;

c) Some Enron emails contain the term `EBITDA`. What happens to this token after case folding? Is this a problem for dictionary-based sentiment analysis?

&nbsp;

&nbsp;

---

## Section D: Stop-Word Removal (Step 4)

**Question 4.**

a) The Step 0 output lists the finance-significant terms present in NLTK's standard stop-word list. Record three of them here, and state their analytical role in financial text.

| Term | Analytical role |
|---|---|
| | |
| | |
| | |

b) In your own words, explain why removing these terms from a corporate email corpus would damage a sentiment analysis.

&nbsp;

&nbsp;

c) For each of the following terms, give an example sentence from financial text in which removing it would distort the meaning or sentiment.

| Term | Example sentence | Effect of removing it |
|---|---|---|
| `not` | | |
| `will` | | |
| `down` | | |

d) Which stop-word setting did you select? Justify your choice with reference to the lecture and the properties of the Enron corpus.

**Choice:** None / Standard NLTK / Finance-adjusted (circle)

**Justification:**

&nbsp;

&nbsp;

---

## Section E: Normalisation (Steps 5 and 6)

**Question 5.**

a) Porter stemming produces `declin` from `declining`. The Loughran-McDonald dictionary holds `decline` but not `declin`. What is the consequence for a sentiment score computed on this corpus?

&nbsp;

b) Find one example in the Step 6 table where lemmatisation preserves an LM dictionary match that stemming does not.

| Token | Porter stem | Lemma | LM match (stem) | LM match (lemma) |
|---|---|---|---|---|
| | | | | |

c) The lecture notes that stemming may be appropriate "when lemmatisation is computationally infeasible." Is computational cost a meaningful constraint for a corpus of 1,000 emails? What would your answer be for a corpus of one million SEC filings?

&nbsp;

&nbsp;

d) Which normalisation method did you select? Justify your choice.

**Choice:** None / Porter Stemming / Lemmatisation (circle)

**Justification:**

&nbsp;

&nbsp;

---

## Section F: The Pipeline Diagnostic (Step 7)

**Question 6.**

a) Record the LM match counts for your pipeline and for the misconfigured pipeline.

| | Your pipeline | Misconfigured pipeline |
|---|---|---|
| LM Positive matches | | |
| LM Negative matches | | |
| Total LM matches | | |

b) By what percentage does your pipeline produce more matches? Which specific decisions account for the difference?

&nbsp;

&nbsp;

c) The net sentiment chart shows LM sentiment across the three periods. Describe the pattern. Does it match what you would expect given Enron's history? Note any surprises.

&nbsp;

&nbsp;

d) Renault (2020) concludes that "algorithm choice explains far less variance than pipeline quality." Based on what you have observed in this exercise, do you find this claim plausible? Explain briefly.

&nbsp;

&nbsp;

---

## Section G: Dictionary Comparison (Step 9)

**Question 7.** Loughran and McDonald (2011) find that between 73% and 80% of the words flagged as negative by the Harvard General Inquirer are not negative in a financial context.

a) The notebook shows terms flagged negative by the Harvard GI but not by LM. List three and explain why they are not negative in a financial document.

| Term | Why not negative in a financial context |
|---|---|
| | |
| | |
| | |

b) List three terms flagged negative by LM but not by the Harvard GI, and explain why they carry negative meaning in corporate disclosure.

| Term | Why negative in a financial disclosure context |
|---|---|
| | |
| | |
| | |

c) Which dictionary would you use for a study of corporate sentiment in SEC filings? Justify your choice.

&nbsp;

&nbsp;

---

## Section H: Corpus Bias (Step 10)

**Question 8.** Apply the six bias types from Section 6.5 of the lecture to the Enron corpus.

| Bias type | Applies? | How |
|---|---|---|
| Resource | Yes / No / Partial | |
| Incentive | Yes / No / Partial | |
| Medium | Yes / No / Partial | |
| Retrieval | Yes / No / Partial | |
| Survivorship | Yes / No / Partial | |
| Self-reporting | Yes / No / Partial | |

**Question 9.** The Step 10 chart shows net LM sentiment broken down by category and period. Does the executive category show the pattern you would predict under incentive bias? Comment on what you observe and what it implies for researchers using corporate disclosure as a measure of firm condition.

&nbsp;

&nbsp;

---

## Section I: Your Pipeline

**Question 10.** Record your final settings and provide a brief justification for each, citing sources where appropriate.

| Decision | Your choice | Justification |
|---|---|---|
| Tokenisation | NLTK `word_tokenize` | |
| Case folding | Yes / No | |
| Punctuation removal | Yes / No | |
| Stop-word list | | |
| Number handling | | |
| Normalisation | | |
| Min document frequency | | |
| Max document frequency | | |

**Question 11.** In no more than 150 words, write a methods paragraph suitable for inclusion in a research paper describing your preprocessing pipeline. Justify each decision with reference to the relevant literature.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

## References

Grimmer, J., Roberts, M.E. and Stewart, B.M. (2022) *Text as Data: A New Framework for Machine Learning and the Social Sciences*. Princeton: Princeton University Press.

Klimt, B. and Yang, Y. (2004) 'The Enron Corpus: A New Dataset for Email Classification Research', *Machine Learning: ECML 2004*, pp. 217-226.

Loughran, T. and McDonald, B. (2011) 'When is a Liability not a Liability? Textual Analysis, Dictionaries, and 10-Ks', *Journal of Finance*, 66(1), pp. 35-65.

Porter, M.F. (1980) 'An algorithm for suffix stripping', *Program*, 14(3), pp. 130-137.

Renault, T. (2020) 'Sentiment analysis and machine learning in finance: a comparison of methods and models on one million messages', *Digital Finance*, 2(1), pp. 1-13.

Todd, A., Bowden, J. and Moshfeghi, Y. (2024) 'Text-based sentiment analysis in finance: synthesising the existing literature and exploring future directions', *Intelligent Systems in Accounting, Finance and Management*, 31.
