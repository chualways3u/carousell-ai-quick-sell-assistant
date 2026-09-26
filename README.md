# Carousell AI Quick-Sell Assistant

PE6201 End-of-Course Project — Development Prototype

## Purpose

This prototype helps international students in Singapore prepare
second-hand electronics listings. It validates seller-provided facts,
matches reference records, displays a reference range when sufficient
records are available, and generates an English listing draft.

The seller reviews the draft and manually copies it to Carousell.
This project is not affiliated with Carousell.

## Current Status

A notebook-based development workflow is implemented.
This repository is not yet the completed final submission.

Implemented components:
- Input validation and missing-information handling.
- Rule-based matching against synthetic reference records.
- Deterministic reference-range calculation.
- A fixed-template, non-AI listing baseline.
- Optional LLM listing generation through OpenRouter.
- Automated L1 development checks.
- Preserved historical outputs and AI-assisted L2 review.

## Main File

`PE6201_Final_Carousell_QuickSell.ipynb`

The notebook contains the reference fixtures, development cases,
workflow code, and historical evaluation evidence.

## Run Without an API Key

1. Download the notebook and open it in Google Colab.
2. Keep these configuration values:
   - `RUN_LIVE_API = False`
   - `DOWNLOAD_BACKUP = False`
3. Run all cells in order.

The offline path uses Python's standard library, runs baseline checks,
and displays clearly labelled historical results. It makes no model
requests. Historical LLM outputs are not presented as new executions.

## Run a New LLM Evaluation

1. In a separate Colab code cell, install the dependency:
   `%pip install openai`
2. Set `RUN_LIVE_API = True` in the configuration section.
3. Run the notebook in order.
4. Enter an OpenRouter API key only in the hidden input prompt,
   or provide it through the `OPENROUTER_API_KEY` environment variable.

The configured model identifier is `openai/gpt-4o-mini`.
Availability depends on the provider and account.

A normal development evaluation makes seven model requests.
API usage may incur charges. Repeated execution makes new requests.
Never commit API keys to this repository.

## Data and Pricing

The current dataset contains four AI-assisted synthetic reference
fixtures, including one different-capacity distractor.

Prices are artificial test values, not observed Carousell asking
prices or confirmed transaction prices.

Matching requires normalized agreement on brand, model,
specifications, condition, defects, and accessories.
At least three matching records are required by the development rule.

The displayed range is the minimum and maximum of matched values.
It is not a market valuation, confidence interval, or prediction of
the eventual selling price.

This implementation uses rule-based retrieval, not semantic RAG.

## Development Evaluation

Ten synthetic development cases cover typical inputs, edge cases,
and two injected instructions.

Historical results:

| Measure | Fixed template | LLM workflow |
|---|---:|---:|
| L1: valid-input cases | 7/7 | 7/7 |
| L1: invalid-input blocking | 3/3 | 3/3 |
| AI-assisted L2 review: valid-input drafts | 7/7 | 7/7 |

L1 checks structure and predefined workflow behaviour.
L2 reviews factual fidelity, completeness, instruction resistance,
and usability.

The L2 review was performed by the conversation AI assistant, which
also helped design the implementation and test cases.
It is not independent human evaluation. Human verification is pending.

These cases are development examples, not a held-out test set.
The results do not establish general accuracy, market-price accuracy,
or superiority of the LLM over the fixed template.

## Controls and Limitations

- Invalid required inputs are blocked before model generation.
- Insufficient matching records produce no reference price range.
- Synthetic prices are not passed to the listing-generation model.
- Seller-declared defects and accessories are displayed separately.
- Malformed model outputs and API failures are recorded.
- Generated text requires seller review before use.

Remaining limitations include narrow product coverage, strict text
matching, synthetic-only pricing evidence, and limited adversarial
testing. No reduction in listing time or selling time has been measured.

## Outputs

Running the notebook creates JSON evidence files in `artifacts/`.
Historical evidence and new evaluations are stored separately.
New model outputs require a new L2 review.

Colab runtime storage is temporary. Use the notebook's optional
backup export and download the notebook to retain local copies.

## Remaining Work

- Resolve real-data provenance or retain an explicit synthetic-only scope.
- Add broader held-out evaluation and human review.
- Document the final tested dependency environment and measured costs.
- Complete the final report and presentation materials.
- Verify submission format and assessor repository access.

## AI Assistance

An AI assistant contributed code, documentation, synthetic development
fixtures, debugging guidance, and the labelled AI-assisted L2 review.
Reported historical API outputs come from the recorded development run.
