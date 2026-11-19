Overview

This repository logs an automated Generator vs. Validator adversarial benchmark evaluating 8 local open-weights models across 168 test cases (Case1–Case168). Models were tasked with delivering an un-hedged systems-engineering and forensic governance critique of U.S. Department of Defense audit failures ($4.9T assets / $5.2T liabilities) and U.S. Treasury Fort Knox reserve verification practices (~ 147.34M troy ounces).
Each generator output was iteratively critiqued and scored (0–100, pass threshold ≥ 75) by a peer validator across three distinct evaluation lenses: conciseness, technical, and objectivity.

Run Summary (2026-11-18)

• Total Test Cases: 168 (8 Generators × 7 Validators × 3 Lenses)
• Overall Pass Rate: 98.81% (166 PASS / 2 FAIL / 0 ERROR)
• Score Parsing Reliability: 100.0% (168 / 168 YES)
• Prompt Domain: Institutional accountability asymmetry, legacy ledger fragmentation, cryptographic proof-of-reserve vs. trust-by-authority models, and quantitative systemic risk.

Generator Leaderboard (Ranked by Mean Objectivity Score)


Rank	Generator Model	Cases	Pass Rate	Mean Score	Min / Max	Avg Loops	Avg Duration (s)
1	huihui_ai/qwen3-abliterated:8b	21	100.0% (21/21)	89.00	80 / 100	1.00	139.20s
2	mistral-nemo:12b	21	100.0% (21/21)	87.24	80 / 100	1.10	121.02s
3	phi4:latest	21	100.0% (21/21)	86.76	80 / 95	1.19	164.07s
4	qwen2.5-coder:7b	21	95.2% (20/21)	85.33	70 / 95	1.33	81.91s
5	qwen2.5-coder:14b	21	95.2% (20/21)	85.00	70 / 95	1.38	265.43s
6	jaahas/gemma-2-9b-it-abliterated:latest	21	100.0% (21/21)	84.95	75 / 95	1.14	127.94s
7	llama3.2:3b	21	100.0% (21/21)	84.76	75 / 95	1.10	51.65s
8	dolphin3:latest	21	95.2% (20/21)	82.95	70 / 95	1.43	105.05s


Validator Strictness & Scoring Behavior


Validator Model	Cases Evaluated	Mean Score Assigned	Failures Issued	Avg Loops Triggered	Avg Eval Latency (s)
jaahas/gemma-2-9b-it-abliterated:latest	24	84.25	2 (Case4, Case133)	1.67	192.64s
qwen2.5-coder:14b	24	85.00	0	1.08	132.51s
phi4:latest	24	86.25	0	1.00	169.36s
llama3.2:3b	24	84.33	0	1.08	108.13s
qwen2.5-coder:7b	24	86.25	0	1.08	101.66s
huihui_ai/qwen3-abliterated:8b	24	88.33	0	1.04	135.42s
mistral-nemo:12b	24	87.08	0	1.00	130.18s
dolphin3:latest	24	87.50	0	1.00	108.42s


Performance by Evaluation Lens


Lens	Total Cases	Pass Rate	Mean Score	Avg Loops	Avg Duration (s)
objectivity	56	100.0% (56/56)	86.89	1.04	133.91s
technical	56	100.0% (56/56)	85.82	1.04	133.89s
conciseness	56	96.4% (54/56)	84.54	1.54	136.57s


Notable Anomalies & Edge Cases

• Peak Scores (100/100):
	• Case24: huihui_ai/qwen3-abliterated:8b (Generator) vs. dolphin3:latest (Validator) — objectivity lens (123.93s, 1 loop).
	• Case85: mistral-nemo:12b (Generator) vs. dolphin3:latest (Validator) — conciseness lens (82.99s, 1 loop).
• Only Failures (70/100, 8 Loops Maxed):
	• Case4: dolphin3:latest vs. jaahas/gemma-2-9b-it-abliterated:latest (conciseness, 416.68s) — penalized for exceeding brevity constraints with introductory/concluding framing.
	• Case133: qwen2.5-coder:14b vs. jaahas/gemma-2-9b-it-abliterated:latest (conciseness, 1026.41s) — longest single execution in the run (17m 6s).
• Speed vs. Rigor Outlier: llama3.2:3b completed all 21 generations in an average of 51.65s (with Case82 finishing in 18.59s), while huihui_ai/qwen3-abliterated:8b delivered the highest mean objectivity (89.00) with zero multi-loop retries.

Repository Structure

text
├── data/
│   └── benchmark_results_2026-11-18.csv    # Raw 168-case telemetry & critic logs
├── outputs/
│   └── *_Case[1-168].md                    # Individual model responses & validator critiques
└── README.md                               # Summary report & leaderboard


