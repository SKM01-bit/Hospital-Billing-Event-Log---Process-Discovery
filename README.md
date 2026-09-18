

Hospital Billing Process Discovery & Structural Analysis

Project Overview
Process discovery, variant profiling, and structural model generation of hospital billing administrative event logs using PM4Py.

Dataset Source
Download the official dataset (3-year Hospital Billing event log, XES format) from 4TU.ResearchData:
[https://data.4tu.nl/datasets/6af6d5f0-f44c-49be-aac8-8eaa5fe4f6fd](https://data.4tu.nl/datasets/6af6d5f0-f44c-49be-aac8-8eaa5fe4f6fd?utm_source=gemini)
Save the file as "Hospital Billing - Event Log.xes.gz" in your local directory or Downloads folder.

Repository Structure

* process_mining_script.py: Main execution script / Jupyter notebook
* README.md: Project documentation
* process_mining_exports/: Generated visual artifacts (DFG, BPMN, Petri Net, Heuristics Net)
* Fig1_DFG.png
* Fig2_BPMN.png
* Fig3_PetriNet.png
* Fig4_HeuristicsMiner.png



Dataset Context

* Domain: Hospital Billing Administration
* Volume: 100,000 cases | 451,359 events
* Scope: 18 distinct lifecycle activities across a 3-year observation window.

Process Discovery & Variant Profile

* Nominal Path: NEW -> FIN -> RELEASE -> CODE OK -> BILLED forms the baseline sequence (Variant 1 accounts for 33.67% of total cases; nominal repeating sequences account for 84.72% of repeating pattern instances).
* Variant Distribution / Early Divergence: Variant 2 (NEW only) represents 22.37% (22,373 cases), reflecting incomplete processing or intake drop-offs. Variant 4 (NEW -> DELETE) accounts for 4.8%.
* Structural Iteration: Recurrent diagnostic re-evaluation loops identified via CHANGE DIAGN (10.07% event occurrence).

Discovered Models & Comparative Methodology

* Directly-Follows Graph (DFG): Captures raw transition frequencies and adjacency weights between hospital billing states.
* Inductive Miner (Petri Net & BPMN): Yields block-structured process models with formal token-based conformance (Fitness: 1.0), establishing strict control-flow bounds.
* Heuristics Miner: Emphasizes empirical dependency thresholds and frequent alternative control-flow loops, illustrating the iterative reality of exception handling.

Requirements & Quickstart
Install dependencies:
pip install pm4py pandas matplotlib graphviz

Run the pipeline:
python process_mining_script.py
(Ensure the dataset path in the script points to your downloaded "Hospital Billing - Event Log.xes.gz").
