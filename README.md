# ml_regression_brendan

This project aims to predict insurance charges based on available data about customers, including age, bmi, and smoking status. First, features are engineered to increase performance. Then different linear regression methods are compared. I conclude that lasso regression performs the best with my chosen features.

GitHub Links
[Fully run notebook](https://github.com/reedbc1/ml_regression_brendan/blob/main/notebooks/ml_regression_brendan.ipynb)
[Peer Review](https://github.com/reedbc1/ml_regression_brendan/blob/main/peer_review.md)

## Local Environment

Run the following to set up your local environment:

```shell
uv python pin 3.12
uv venv
uv sync --extra dev --extra docs --upgrade
uv run pre-commit install
uv run python --version
```

**Windows (PowerShell):**

```shell
.\.venv\Scripts\activate
```

**macOS / Linux / WSL:**

```shell
source .venv/bin/activate
```

---

You can then run the notebook (notebooks/ml_regression_brendan.ipynb) locally.
