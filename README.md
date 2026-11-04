# Smart Savings

An ICT 336 workshop application built with Streamlit and two saved machine learning models.

- **Fixed deposit:** estimates the probability that a customer will open a fixed deposit after a bank call.
- **Saver group:** uses K-Means to group customers by annual income and spending score, then displays a savings tip and customer chart.
- **About the models:** displays the model information and scores included with the project.

This application is for teaching purposes and is not financial advice.

## Run locally

Use Python 3.12 and run the following commands from the project folder.

On Windows (PowerShell):

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m streamlit run app.py
```

On macOS or Linux:

```bash
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m streamlit run app.py
```

Open the local URL printed by Streamlit. Run from the project folder so the application can find the model and CSV files.

## Project files

| File | Purpose |
| --- | --- |
| `app.py` | Streamlit application |
| `requirements.txt` | Python dependencies; scikit-learn is pinned to 1.6.1 |
| `savings_model.joblib` | Saved fixed-deposit prediction model and metadata |
| `saver_model.joblib` | Saved customer-group model and metadata |
| `customers_with_groups.csv` | Customer income, spending scores, and assigned groups |

The saved models are included, so no training step is needed to start the application. Training code and the original training datasets are not included.

## Dataset references

The application credits these Kaggle datasets:

- Bank Marketing: `henriqueyamahata/bank-marketing`
- Mall Customer Segmentation Data: `vjchoudhary7/customer-segmentation-tutorial-in-python`
