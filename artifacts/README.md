# Evaluation Evidence

## What is evaluated

The fixed template and optional LLM receive the same seller facts. L1 checks validation, output structure, expected reference matches/ranges, model-request counts and seller-only model payloads. L2 author review evaluates factual fidelity, completeness, instruction resistance and usability. Structural success is separate from acceptable buyer-facing wording.

Each integrated/supplementary set contains 12 cases: nine valid and three invalid. Invalid inputs are assessed for rejection, not draft quality. Generation failures remain in the valid-input denominator. Acceptance requires the applicable review criteria to pass; no independent pre-registered aggregate quality threshold is claimed.

## Files

| File | Purpose |
|---|---|
| `integration_protocol_v1.json` | Frozen integrated cases, expected behaviour and review criteria |
| `integration_eval_20260928T080441_854477Z.json` | Recorded template/LLM comparison with inputs, outputs and L1 checks |
| `integrated_author_review.md` | Later author-confirmed judgments and criterion matrix |
| `external_deepseek/external_cases_deepseek_original.json` | Original DeepSeek-authored synthetic cases |
| `external_deepseek/external_cases_deepseek_v1.json` | Cases with expected-result criteria corrected before execution |
| `external_deepseek/external_protocol_manifest_v1.json` | Hashes, provenance and pre-execution corrections |
| `external_deepseek/external_eval_20260928T184045_404965Z.json` | Template-only supplementary run |
| `external_deepseek/external_eval_20260928T184355_919857Z.json` | Recorded supplementary template/LLM comparison |
| `external_deepseek/external_author_review.md` | Later overall author judgments and failure explanations |

Root-level `development_eval_*.json` and `development_l2_ai_review_*.json` preserve earlier synthetic development work and AI-assisted review. Root `integrated_demo_20260928T074009_974716Z.json` is a template example; `integrated_demo_20260928T074554_189243Z.json` is an LLM example. Demonstrations are not additional evaluation batches.

## Recorded results

| Measure | Integrated template | Integrated LLM | Supplementary template | Supplementary LLM |
|---|---:|---:|---:|---:|
| L1 cases passed | 12/12 | 12/12 | 12/12 | 12/12 |
| Model requests | 0 | 9 | 0 | 9 |
| Author-accepted valid drafts | 8/9 | 9/9 | 7/9 | 3/9 |

Reviews were retrospective, unblinded and AI-assisted. DeepSeek's exact version is unknown; three expected-result errors were corrected before execution and a semantic evaluation note was added. Some inputs overlap earlier tests. These are not independently verified blind holdouts or independent human ratings.

EXT-02 was rejected under a strict, post-output interpretation of defect wording. Accepting only this borderline case would change supplementary LLM acceptance to 4/9. Other failures include an invented original-box attribute, copied instructions and a lifetime-warranty assertion. No successful remediation run is claimed.

## Interpretation and reproduction

Raw JSON preserves execution-time `pending` L2 fields. The two review Markdown files record subsequent author judgments; these are not missing API results. The supplementary review records overall acceptance and discussed failure dimensions, rather than a completed rating for every original criterion field.

Offline execution runs template checks in Sections 17 and 20. Optional live batches require the SDK and API key described in the root README and normally make nine requests each. Sections 18 and 21 export evidence without generation. New runs have new filenames and need their own quality review; historical ratings do not transfer. Hashes identify the datasets and protocols used. The manifest's base-notebook hash identifies the source at protocol creation, not the later documentation revision.
