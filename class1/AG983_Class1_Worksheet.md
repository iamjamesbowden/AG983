# AG983: Textual Analytics for Accounting and Finance
## Class 1 Workshop Worksheet — Text Pre-Processing: Decisions and Consequences

**Name:** _____________________________ &nbsp;&nbsp;&nbsp;&nbsp; **Date:** _____________________________

---

This worksheet accompanies the Class 1 Colab notebook. Complete each question as you work through the notebook, recording your observations, choices, and justifications. Submit this as a Word document.

---

### Background: The Enron Corpus

The corpus used in this workshop is drawn from the Enron email dataset (Klimt & Yang, 2004), released into the public domain by the Federal Energy Regulatory Commission (FERC) during the 2001 investigation into Enron Corporation.

The corpus spans three periods:
- **Pre-crisis (2000):** Enron at peak performance, named Fortune's Most Innovative Company for the fifth consecutive year
- **Crisis (2001):** Accounting irregularities emerge; share price collapses from $90 to under $1
- **Collapse (late 2001–2002):** Bankruptcy filing; regulatory investigations; employee savings wiped out

As discussed in the lecture, this corpus is particularly well-suited to preprocessing exercises because it combines the *hedged, forward-looking register of corporate financial communication* with the *informal directness of internal correspondence*.

---

## Section A: Corpus Exploration (Step 1)

**Question 1.** After running Step 1 in the notebook, answer the following:

a) How many emails are in the corpus, and how are they distributed across the three time periods?

&nbsp;

&nbsp;

b) What is the mean email length in words? What is the shortest and longest email? What does this variation in length suggest about the register diversity of the corpus?

&nbsp;

&nbsp;

c) Look at the raw text of one email printed by the notebook. Identify at least **three preprocessing challenges** visible in the raw text (e.g. punctuation attached to words, mixed case, numbers embedded in text).

| # | Preprocessing challenge | Example from the text |
|---|---|---|
| 1 | | |
| 2 | | |
| 3 | | |

---

## Section B: Tokenisation (Step 2)

**Question 2.** The notebook compares whitespace tokenisation against NLTK's `word_tokenize`.

a) How many more or fewer tokens does NLTK produce compared to whitespace splitting for the sample email?

&nbsp;

b) The Loughran-McDonald dictionary contains the word `liability`. If a document contains the string `"liabilities."` (with punctuation attached), will a whitespace tokeniser match it against the dictionary? Explain why or why not.

&nbsp;

&nbsp;

c) Why does this matter for the reliability of a sentiment score computed from a corporate disclosure?

&nbsp;

&nbsp;

---

## Section C: Case Folding and Punctuation Removal (Step 3)

**Question 3.**

a) Examine the four frequency distributions shown in the notebook. What is the most obvious change between "no processing" and "case-fold + punctuation removed"?

&nbsp;

b) The lecture noted that retaining `!` and `?` improves financial sentiment classification accuracy by 0.3% (Renault, 2020). For a corpus of corporate email like Enron, would you retain or remove these characters? Justify your answer.

&nbsp;

&nbsp;

c) The Enron corpus includes emails like `"EBITDA margins improved"`. What happens to the token `EBITDA` after case folding? Is this a problem for financial text analysis?

&nbsp;

&nbsp;

---

## Section D: Stop-Word Removal (Step 4)

**Question 4.** This is one of the most consequential decisions in preprocessing financial text.

a) In your own words, explain why the standard NLTK stop-word list is inappropriate for sentiment analysis of corporate disclosures.

&nbsp;

&nbsp;

b) The notebook shows that the standard NLTK list removes `will`, `may`, `not`, and `down`. For each of these, give an example sentence from financial text where removing it would distort the sentiment or meaning:

| Term | Example sentence | Effect of removal |
|---|---|---|
| `will` | | |
| `may` | | |
| `not` | | |
| `down` | | |

c) Which stop-word setting did you choose for your pipeline? Justify your choice with reference to the lecture material and the specific properties of the Enron corpus.

**My choice:** ☐ None &nbsp; ☐ Standard NLTK &nbsp; ☐ Finance-adjusted

**Justification:**

&nbsp;

&nbsp;

---

## Section E: Normalisation — Stemming vs Lemmatisation (Steps 5–6)

**Question 5.**

a) The notebook shows that Porter stemming produces `liabil` from `liability`. The Loughran-McDonald dictionary contains `liability`. What is the consequence for your sentiment score?

&nbsp;

b) Find one example in the comparison table (Step 6) where lemmatisation preserves a meaningful LM dictionary match that stemming would destroy. Record it here:

| Token | Stem | Lemma | LM match: raw | LM match: stem | LM match: lemma |
|---|---|---|---|---|---|
| | | | | | |

c) The lecture noted that stemming may be defensible "when lemmatisation is computationally infeasible." Given that the Enron corpus has 1,000 emails, is computational cost a meaningful constraint here? What would your answer be for a corpus of 500,000 10-K filings?

&nbsp;

&nbsp;

d) Which normalisation method did you choose? Justify your choice.

**My choice:** ☐ None &nbsp; ☐ Porter Stemming &nbsp; ☐ Lemmatisation

**Justification:**

&nbsp;

&nbsp;

---

## Section F: The Pipeline Diagnostic (Step 7)

**Question 6.** This step directly illustrates the consequences of your choices.

a) How many LM positive and negative matches did your pipeline produce? How does this compare to the misconfigured pipeline?

| | Your pipeline | Misconfigured pipeline |
|---|---|---|
| LM Positive matches | | |
| LM Negative matches | | |
| Total LM matches | | |

b) The chart in Step 7 shows net LM sentiment across the three periods (pre-crisis, crisis, collapse). Describe the pattern you observe. Does the direction of the change make sense given what you know about Enron's history?

&nbsp;

&nbsp;

c) Renault (2020) finds that "algorithm choice explains far less variance than pipeline quality." Based on what you have seen in this exercise, do you find this claim plausible? Explain.

&nbsp;

&nbsp;

---

## Section G: Dictionary Comparison (Step 9)

**Question 7.** Loughran & McDonald (2011) demonstrate that between 73% and 80% of negative words identified by the Harvard General Inquirer are not negative in a financial context.

a) The notebook shows tokens flagged as negative by the Harvard GI but not by LM. List three such tokens visible in the notebook output and explain why they would be incorrectly classified as negative in a financial document:

| Token | Why not negative in financial context |
|---|---|
| | |
| | |
| | |

b) Examine the tokens flagged as negative by LM but not by Harvard GI. These represent finance-specific negative language. List three examples and comment on why they carry negative meaning in corporate disclosure:

| Token | Why negative in financial context |
|---|---|
| | |
| | |
| | |

---

## Section H: Corpus Bias (Step 10)

**Question 8.** Apply the six bias types from Section 6.5 of the lecture to the Enron corpus used in this workshop:

| Bias type | Does it apply to this corpus? | Explain specifically how |
|---|---|---|
| **Resource bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Incentive bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Medium bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Retrieval bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Survivorship bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |
| **Self-reporting bias** | ☐ Yes &nbsp; ☐ No &nbsp; ☐ Partial | |

**Question 9.** The chart at the bottom of Step 10 shows net LM sentiment across the three Enron periods. Managers wrote more positively during the crisis than the financial reality warranted.

Which bias type best explains this pattern, and what does it imply for researchers who use corporate disclosures as a measure of firm condition?

&nbsp;

&nbsp;

&nbsp;

---

## Section I: Your Final Pipeline

**Question 10.** Record your final pipeline settings and justify each choice.

| Decision | Your choice | Academic justification |
|---|---|---|
| Tokenisation | NLTK `word_tokenize` | |
| Case folding | ☐ Yes &nbsp; ☐ No | |
| Punctuation removal | ☐ Yes &nbsp; ☐ No | |
| Stop-word list | | |
| Number handling | | |
| Normalisation | | |
| Min document frequency | | |
| Max document frequency | | |

**Question 11.** In no more than 150 words, write a methods paragraph that could appear in a research paper describing your pre-processing pipeline. Follow the conventions of academic writing — justify each decision with reference to relevant literature.

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
