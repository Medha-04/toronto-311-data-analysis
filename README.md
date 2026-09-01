# What annoys each part of Toronto?

Exploratory analysis of Toronto 311 service requests, comparing **frequency** and **distinctiveness** across Toronto's 25 wards.

## Run locally

1. Download the 311 Service Requests - Customer Initiated data from the City of Toronto:
   https://open.toronto.ca/dataset/311-service-requests-customer-initiated/
2. Place the 2026 CSV at `data/SR2026.csv`.
3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Open `toronto_311.ipynb` in Jupyter or VS Code and run all cells.

## Analysis

The notebook asks three related questions:

- What are Toronto's most frequently reported 311 requests?
- Which complaints are unusually prominent in particular wards?
- Do those patterns reveal broader geographic structure?

The main metric is **distinctiveness**:

`ward share of complaint / citywide share of complaint`

A value of 1.0x means the complaint has the same share locally as it does across Toronto. Values above 1.0x indicate greater local prominence.

## Data handling

The raw CSV is intentionally not included in the repository. It is large and is available from the City of Toronto Open Data Portal. The notebook explicitly repairs the two malformed row structures observed in the supplied 2026 file and raises an error for unexpected structures rather than silently dropping records.

## Important caveat

311 requests measure **reporting behaviour**, not the true prevalence of an underlying problem. Results are descriptive and should not be interpreted as causal.

The open 311 dataset also represents only a subset of total 311 activity.

## Outputs

The notebook writes:

- `outputs/toronto_311_clean.csv`

This file contains the cleaned request-level data plus ward-level fields used by the Tableau visualizations.
