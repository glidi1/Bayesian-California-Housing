# Bayesian and Decision Modelling with pyAgrum: California Housing

Coursework for ECS647U/773P Bayesian Decision and Risk Analysis (MSc Advanced Computer Science, Queen Mary University of London).

The notebook builds a Bayesian network from the 1990 California Housing census data, uses it for observational, interventional and counterfactual reasoning, then extends it into an influence diagram to compare investment and renovation decisions.

## What the notebook does

| Section | Content |
|---|---|
| Q1 | Load the dataset, pick six variables, discretise each into three quantile-based bins |
| Q2 | Learn the network structure with Greedy Hill Climbing (BDeu), with two mandatory arcs from domain knowledge (Income to HouseValue, Income to RoomSize) |
| Q3 | Inspect the CPTs for root, leaf, intermediate and multi-parent nodes, learned by maximum likelihood |
| Q4 | Observational, interventional (`do`-operator) and counterfactual reasoning |
| Q5 | Extend the network into an influence diagram with 2 decision nodes and 2 utility nodes |
| Q6 | Solve the influence diagram, compare all six decision combinations by expected utility |
| Q7 | Summary of model size and key results |

## Variables

| Variable | Source column | States |
|---|---|---|
| Income | MedInc | Low / Medium / High |
| HouseAge | HouseAge | New / Mid / Old |
| RoomSize | AveRooms | Small / Medium / Large |
| Occupancy | AveOccup | Low / Medium / High |
| Population | Population | Sparse / Moderate / Dense |
| HouseValue | MedHouseVal | Cheap / Moderate / Expensive |

## Decision model

- **Decisions:** `InvestDecision` (Buy, Hold, Sell) and `RenovateDecision` (Renovate, NoRenovate)
- **Utilities:** `FinancialReturn` (depends on investment decision and house value) and `RiskCost` (depends on renovation decision, house age and occupancy)

The utility values are hand-set assumptions for the coursework, not estimates from real market data.

## Running it

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
jupyter notebook Bayesian_CW_Notebook.ipynb
```

Run the cells in order. The dataset is fetched through scikit-learn, so no manual download is needed. The first run writes `california_housing_disc.csv`, which later cells read back in.

## Tech

Python, pyAgrum, pandas, NumPy, scikit-learn, Jupyter

## Dataset

California Housing Prices (1990 US Census), loaded with `sklearn.datasets.fetch_california_housing`. 20,640 rows.

## Author

Elidian Terziu
[LinkedIn](https://linkedin.com/in/elidian-terziu)
