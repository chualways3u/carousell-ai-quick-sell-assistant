# Carousell AI Quick-Sell Assistant

PE6201 End-of-Course Project — Individual Prototype

## Purpose

Preparing a second-hand listing involves two practical tasks: finding relevant price references and describing the item clearly. For international students and young working professionals in Singapore, these tasks can be especially inconvenient when moving, graduating or leaving the country.

Carousell AI Quick-Sell Assistant brings **reference offers and English draft writing into one workflow**. Sellers enter their item's details, view matching commercial asking prices and receive a listing draft to review and copy to Carousell. The goal is to make listing preparation easier while keeping the seller in control of the final wording and asking price.

The working prototype focuses its reference data on **iPhone 13 128GB**. It combines a reproducible template baseline with optional AI writing and recorded evaluations. 

## What the Prototype Does

1. **Collects seller facts:** brand, model, storage, condition, defects and accessories.
2. **Validates inputs:** blocks missing or invalid required information before generation.
3. **Finds reference offers:** matches brand, model and capacity against a documented snapshot.
4. **Prepares an English draft:** uses a fixed template by default or optional LLM generation.
5. **Supports seller review:** displays seller facts and reference context before the seller manually copies a draft to Carousell.

The reference range supports comparison; it is not a recommended private-sale price. Listing preparation time and selling outcomes have not yet been measured.

## Main File

`PE6201_Final_Carousell_QuickSell.ipynb`

- Sections 2–11: earlier synthetic development tests and historical outputs.
- Sections 12–15: real reference snapshot and integrated demonstration.
- Sections 16–18: integrated evaluation and export.
- Sections 19–21: DeepSeek supplementary evaluation and export.

## Run in Colab

**Offline demonstration**

Open the notebook in Colab, keep all API and download switches `False`, and run all cells. View Section 14 for the template demonstration, Section 17 for integrated template checks and Section 20 for supplementary template checks. No API key is needed. Historical LLM outputs remain labelled as saved results.

**One live AI draft**

Install the recorded SDK version in a separate cell:

```python
%pip install openai==2.54.0
```

Set `DEMO_USE_LLM = True` in Section 1. Keep `RUN_LIVE_API`, `RUN_INTEGRATED_LLM_EVAL` and `RUN_EXTERNAL_LLM_EVAL` false. Run through Section 14 and enter the OpenRouter key in the hidden prompt. A valid demonstration makes one request to `openai/gpt-4o-mini`. Never commit API keys.

**Optional evaluation reruns**

After offline setup and SDK installation, enable only the desired batch switch: `RUN_INTEGRATED_LLM_EVAL` in Section 17 or `RUN_EXTERNAL_LLM_EVAL` in Section 20. Run that cell once; each normally makes nine requests. `RUN_LIVE_API` controls the older seven-request development batch.

Recorded live runs used Python 3.13.15 and OpenAI SDK 2.54.0. Course-provided credits covered the author's API usage; calls still consume credits. Provider availability and Colab environments may change.

## Data and Pricing

The author collected three commercial Carousell Singapore iPhone 13 128GB asking-price observations on **27 September 2026**, with source URLs and screenshots:

| Colour | Observed asking price |
|---|---:|
| Pink | SGD 338 |
| Midnight | SGD 344 |
| Starlight | SGD 348 |

These are dated merchant offers, not transaction prices. Condition, battery health, accessories and warranty differ; seller claims have not been independently verified.

Retrieval uses normalized brand, model and storage capacity. It is **rule-based retrieval**, not semantic RAG. Condition and accessories are context, not matching filters. The range is the minimum and maximum of available matching prices; no match means no range. There is no three-record threshold, and `recommended_price_sgd` remains null.

Section 12 loads `data/iphone13_reference_listings.json`, then `iphone13_reference_listings.json`, or uses the embedded snapshot if neither exists. Invalid external data raises an error. Synthetic test inputs and earlier synthetic price fixtures are separate from these real observations.

## Recorded Evaluation

Two 12-case sets compare the template and LLM, each with nine valid and three invalid inputs.

| Measure | Integrated template | Integrated LLM | DeepSeek template | DeepSeek LLM |
|---|---:|---:|---:|---:|
| Automated L1 cases passed | 12/12 | 12/12 | 12/12 | 12/12 |
| Model requests | 0 | 9 | 0 | 9 |
| Author-accepted drafts | 8/9 | 9/9 | 7/9 | 3/9 |

The evaluations informed the design: retain the template as the default and offer AI writing with seller review. L1 verifies structure and workflow; author review checks draft quality. Supplementary tests identified unsupported original-box and warranty claims and copied attack instructions.

Reviews were retrospective, unblinded and AI-assisted. DeepSeek's exact version was not supplied; three errors in its expected-result criteria were corrected before execution. Some cases overlap earlier tests, so this is not an independent blind holdout. EXT-02 was a borderline defect-wording rejection; accepting that case alone would change supplementary LLM acceptability to 4/9. These results describe the tested cases, not general accuracy.

Raw JSON retains execution-time pending review fields. Completed author judgments are recorded in:

- `artifacts/integrated_author_review.md`
- `artifacts/external_deepseek/external_author_review.md`

## Controls and Limits

Implemented controls include required-input validation, a six-field input allowlist, restrictive generation prompts, separate seller-fact display, output-schema checks and error logging. Merchant prices and warranties are excluded from the listing model's input. Publishing remains a manual seller action.

These controls support a supervised prototype; they do not catch every unsupported claim or injected instruction. Seller review is necessary and is not enforced by an approval gate. Next steps are stronger claim verification and user testing of listing preparation time.

## Evidence and Export

Results are saved under `artifacts/`, with supplementary runs in `artifacts/external_deepseek/`. Sections 15, 18 and 21 export evidence without repeating generation. Preserve failed attempts as well as successful runs. Download the executed notebook separately because Colab runtime storage is temporary.

## Individual Work and AI Assistance

I personally collected the webpage evidence, ran the notebook and API evaluations, and saved and uploaded project files. AI assistance supported code, documentation, debugging and test design, and the labelled AI-assisted L2 review. Reported historical API outputs come from the recorded development run. The earlier AI-assisted L2 review is not independent human evaluation. I remain responsible for verifying the submitted work.
