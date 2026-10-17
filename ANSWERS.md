# Midterm 1: answers

GitHub username:baltabaysauryzhan
Session code:KETTLE-62
Fingerprint:57229920

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A |0,4000 |0,6167 |0,7167 |0,5284 |
| B | 0,2500|0,5833 |0,7000 |0,4357 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 |61,7% |49,1% |72,9% |
| A, k=5 |71,7% |59,2% |81,5% |
| B, k=3 |58,3% |45,8% |69,8% |
| B, k=5 |70% |57,5% |80,1% |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 |$3923,47 |
| A, k=5 |$5,463.80 |
| B, k=3 |$2,319.46 |
| B, k=5 |$2,790.45 |

### 1d. Decision (at most 150 words)

Chosen candidate:(A, 5)

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)
Candidate (A, 5) achieves the highest recall of 71.7% (95% CI [59.2%, 81.5%]) and fits comfortably within the $8,200 annual budget at $5,463.80. Per-language recall for (A, 5) is: EN 80.0% (16/20), RU 75.0% (15/20), and KK 60.0% (12/20). Kazakh (KK) is served worst because longer tokenizer representations limit the semantic overlap per retrieval window.

### 1e. Next measurement (at most 60 words)

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H |89,4% |KK, degraded |83,3% |66,4% |92,7% |$26013,29 |
| L |80% |KK, clean & degraded |73,3% |55,5% |85,8% |$5400,00 |

Personal-data pages per year sent abroad under H: 766,500

### 2b. Memo (at most 300 words)
**Performance & Accuracy:** Pipeline H delivers superior accuracy (88.33%) compared to L (79.44%). Both struggle most with Kazakh degraded scans (H: 83.3%, L: 73.3%).

**Legal & Personal Data Sovereignty:** Under Law No. 94-V, handling personal data (names, IINs) requires strict governance. Pipeline H transmits 766,500 pages with PII abroad annually to a foreign data center. Storage location, duration, and vendor access are outside local jurisdiction. Pipeline L processes all data locally on bank servers.

**Safeguards:** For H, implement an automated local PII-masking layer prior to cloud submission. For L, enforce immutable audit logging and strict access controls.

**Recommendation:** Choose **Pipeline L**. Although its accuracy is lower, it guarantees compliance with Kazakhstan's personal data law and saves significant budget ($5,400 vs $26,013). Residual risk (unextracted fields on degraded scans) is mitigated via manual fallback verification for low-confidence documents.

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
