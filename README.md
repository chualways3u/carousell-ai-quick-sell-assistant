Carousell AI Quick-Sell Assistant
PE6201 End-of-Course Project — Individual Prototype
Purpose
Help international students and young working professionals in Singapore prepare English second-hand listings using seller facts and commercial reference offers. The seller checks the draft and manually copies it to Carousell. This project is not affiliated with Carousell.
Main File
PE6201_Final_Carousell_QuickSell.ipynb
- Sections 2–11: earlier synthetic development tests and historical outputs.
- Sections 12–15: real reference data and integrated demonstration.
- Sections 16–18: integrated evaluation and evidence export.
Run in Colab
Offline demonstration
1. Open the notebook in Google Colab.
2. Keep all API and download switches False, including RUN_LIVE_API, DEMO_USE_LLM and RUN_INTEGRATED_LLM_EVAL.
3. Run all cells. View the demonstration in Section 14 and template evaluation in Section 17. No model requests are made.
One live LLM demonstration
1. First install the tested SDK in a separate cell: %pip install openai==2.54.0.
2. Set DEMO_USE_LLM = True; keep RUN_LIVE_API and RUN_INTEGRATED_LLM_EVAL false.
3. Run the notebook and enter the OpenRouter key in the hidden prompt. View Section 14.
A valid live demonstration makes one request to openai/gpt-4o-mini. Course-provided API credits cover this project's usage at no personal cost to the student; requests still consume credits. Never commit API keys.
Data and Pricing
I collected three Carousell Singapore commercial iPhone 13 128GB offers on 27 September 2026: Pink at SGD 338, Midnight at SGD 344, and Starlight at SGD 348. Source URLs and screenshots support these observed asking prices; they are not confirmed transaction prices.
Section 12 loads data/iphone13_reference_listings.json or iphone13_reference_listings.json, falling back to the embedded snapshot only when neither file exists.
Retrieval matches normalized brand, model and storage capacity. Condition, battery health, accessories and warranty differ. The displayed range is the minimum and maximum of matching offers. No match means no range; there is no three-record minimum. The system provides no private-sale price recommendation.
This is rule-based retrieval, not semantic RAG. Earlier synthetic price fixtures test software logic only and are separate from the real reference data.
Integrated Evaluation
The recorded batch uses 12 constructed test cases: nine valid and three invalid inputs.
Measure	Template	LLM
Automated L1 cases passed	12/12	12/12
Model requests	0	9
Integrated L2 human review	Pending	Pending


L1 checks predefined workflow behavior and output structure, not general factual accuracy. These author-designed cases are not an independent holdout. Earlier AI-assisted L2 reviews are historical, not current human ratings.
To repeat the integrated live batch after offline setup and SDK installation, leave the other API switches false, set RUN_INTEGRATED_LLM_EVAL = True in Section 17 and run that cell. This normally makes nine requests. RUN_LIVE_API controls the older seven-request development evaluation.
Recorded environment: Python 3.13.15; OpenAI SDK 2.54.0.
Controls and Limitations
Invalid required inputs are blocked. Only six seller fields reach the model; reference prices and merchant warranties are excluded. Prompts require declared defects and accessories and prohibit invented claims. Output checks record malformed responses and API failures; seller review remains necessary.
Limitations include three commercial references, unverified seller claims, stale-price risk and incomplete quality evaluation. Instructions inside permitted fields remain a risk. No improvement in listing time, selling time or pricing accuracy has been demonstrated.
Outputs and Remaining Work
JSON results are saved in artifacts/. Section 15 downloads the demonstration; Section 18 exports integrated evaluation evidence. Download the notebook separately because Colab storage is temporary.
Before submission: synchronize the latest notebook and evidence, complete outstanding evaluation, verify reproducibility and assessor access, finalize the analysis of no more than 1,200 words, and record the presentation/demo.
Individual Work and AI Assistance
I personally collected the webpage evidence, ran the notebook and API evaluations, and saved and uploaded project files. AI assistance supported code, documentation, debugging and test design. The earlier AI-assisted L2 review is not independent human evaluation. I remain responsible for verifying the submitted work.
