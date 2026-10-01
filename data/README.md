# Reference Data

## Source and purpose

`iphone13_reference_listings.json` contains three commercial Carousell Singapore iPhone 13 128GB offers recorded by the author on 27 September 2026. Their asking prices are SGD 338 (Pink), 344 (Midnight) and 348 (Starlight). Source URLs and listing IDs identify the offers. The observations support reference-price display, not transaction-price prediction.

The author collected webpage screenshots; the JSON contains transcribed observations. Screenshots are not included in this repository snapshot. The `evidence_screenshots` entries identify separately collected evidence rather than files bundled here. Prices, stock and seller claims may change; condition, battery health and warranties were not independently verified.

## Schema

| Fields | Meaning |
|---|---|
| `dataset_version`, `observed_date_sgt` | Snapshot version and collection date in Singapore |
| `collection_method`, `price_type`, `currency`, `scope`, `limitations` | Collection context and interpretation boundaries |
| `records` | List of three commercial observations |
| `listing_id`, `source_url` | Source identifiers |
| `brand`, `model`, `storage_gb`, `colour` | Product identity; storage is numeric GB |
| `asking_price_sgd` | Observed merchant asking price in Singapore dollars |
| Seller name fields, `seller_type` | Recorded merchant identity/type |
| `seller_condition_rating`, `screen_description`, `body_description` | Seller descriptions, not an independent inspection |
| `battery_health_display_pct` | Reported battery percentage |
| `included_accessories`, `seller_warranty`, `manufacturer_warranty` | Offer-specific inclusions and warranty statements |
| `evidence_screenshots` | References to separately collected source screenshots |

## Loading and matching

Notebook Section 12 validates the external JSON and prints its source and SHA-256. It checks `data/iphone13_reference_listings.json`, then a same-named file in the working directory; when neither exists, it uses the identical embedded snapshot. Malformed external data raises an error.

Section 13 matches normalized brand and model plus storage capacity. Other offer attributes are displayed as context, not filters. A match yields the minimum and maximum asking prices; no match yields no range. `recommended_price_sgd` remains null. This is structured rule-based retrieval.

## Real observations versus synthetic tests

The three records above are observed offers. Seller examples and evaluation inputs are synthetic, not actual users or transactions. Earlier notebook Sections 2–11 also contain synthetic price fixtures for testing software logic; those values are not real market evidence. Evaluation datasets and their explanations are in [artifacts](../artifacts/README.md).
