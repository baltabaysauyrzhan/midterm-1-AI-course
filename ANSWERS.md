# Midterm 1: answers

GitHub username:baltabaysauryzhan
Session code:KETTLE-62
Fingerprint:57229920

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)
## Declaration on the Use of AI
I used a Gemini to better grasp the nature of intermediate tasks, verify mathematical calculations, and provide step-by-step explanations of the problems. Also to calculate all search metrics (such as recall and Wilson score confidence intervals), determine the precise costs of the models, and assess the budget constraints for the pipeline—all based on my personal dataset—I utilized a Python runtime environment in Google Colab. 

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A |0,4000 |0,6167 |0,7167 |0,5284 |
| B | 0,2500|0,5833 |0,7000 |0,4357 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 |76,7% |64,6% |85,6% |
| A, k=5 |85% |73,9% |91,9% |
| B, k=3 |51,7% |39,3% |63,8% |
| B, k=5 |76,7% |64,6% |85,6% |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 |$9,243.59|
| A, k=5 |$12,256.02|
| B, k=3 |$6,200.24|
| B, k=5 |$7,183.76 |

### 1d. Decision (at most 150 words)

Chosen candidate:(B, 5)

(Decision, using your intervals and the budget. Give the recall of your choice for EN, RU and KK separately.)

Candidate (B, 5) is our best choice because both config A options cost $9,243 and $12,256 which are over our $8,200 annual budget. Candidate (B, 5) costs $7,183.76 so it stays inside budget and gives us good recall at 76.7% with 95% confidence interval [64.6%, 85.6%]. Looking at languages separately for option (B, 5), English recall is 80.0%, Russian is 75.0% and Kazakh is 70.0%. Kazakh language is served worst here because its longer token representations limit how much context fits in the retrieval window.

### 1e. Next measurement (at most 60 words)
We should test real user answers using LLM with retrieved context to see if higher retrieval recall actually makes the final model answers more accurate for users.

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H |89,4% |KK, degraded |83,3% |66,4% |92,7% |$23,454.90 |
| L |80% |KK, clean |73,3% |55,5% |85,8% |$5,400.00 |

Personal-data pages per year sent abroad under H: 766,500

### 2b. Memo (at most 300 words)

Pipeline H gets better total accuracy at 89.44% than Pipeline L at 80.00%. Both pipelines do worst on Kazakh degraded scans with 83.3% accuracy for H and 73.3% for L. But under Law No. 94-V on personal data, Pipeline H sends 766,500 pages with personal info like names and IIN abroad every year to foreign cloud servers. We do not fully know where the scan goes, who stores it or for how long. Pipeline L keeps all data inside Kazakhstan on our own server. For safeguards we could automatically hide IIN numbers before sending images to H, or keep strict access logs for L. I choose Pipeline L because it protects personal data and saves money at $5,400 per year instead of $23,454. The remaining risk is lower accuracy on bad scans, which human workers can check manually.

## Part 3: Explain your own numbers

### Q1

Number:1.54
Why (at most 40 words): The ratio being higher than 1 shows that Kazakh token costs come from tokenizer vocabulary splits rather than UTF-8 character encoding.

### Q2

Number:851
Why (at most 40 words): No, because the answer sentence starts at token 851 which is past the 512 token e5 limit, so it is cut off and invisible to the model.

### Q3

Number:91.7%
Why (at most 40 words): Changing T to 0.5 made the top score gap wider and increased top probability, but it did not change token ranking or the set of sampleable tokens. 

### Q4

Number:23%
Why (at most 40 words): We left out arithmetic sequences and multiplication because base models can compute rules dynamically. System prompts cannot fix missing facts.

### Q5

Number:15.45
Why (at most 40 words): The model is over-trained. Chinchilla showed models like GPT-3 were significantly under-trained relative to their compute-optimal token budget.
