# AI News Topic Modelling with NMF and LDA

A natural language processing project exploring themes in news coverage of artificial intelligence (AI) using **The Guardian Open Platform API**, **Non-negative Matrix Factorisation (NMF)** and **Latent Dirichlet Allocation (LDA)**.

## Project overview

- **Research question:** What recurring themes appear in Guardian news coverage connected with AI?
- **Source:** The Guardian Open Platform API (news articles published between January 2018 and December 2024).
- **Search queries:** `artificial intelligence`, `AI regulation`, `machine learning`.
- **Methods:** collection and cleaning, exploratory data analysis (EDA), stopword removal and lemmatisation, TF-IDF + NMF, count vectors + LDA, and comparisons of topic interpretability and training times.
- **Environment:** Jupyter / Google Colab or local Python.

## Files

| File | Purpose |
| --- | --- |
| `guardian_ai_news_topic_modelling.ipynb` | Main notebook: Guardian data collection, cleaning, EDA, NMF, LDA, and comparison. |
| `model_training_times.csv` | Training times reported from the original assessment in cloud and local environments. |
| `requirements.txt` | Python package dependencies. |
| `.gitignore` | Excludes credentials, virtual environments, caches and downloaded datasets. |

The original assessment PDF is **not included** because its cover page contains personal student information. The original `Read Me.txt` is not included because it contained an API credential.

## Running the notebook

1. Download this repository and install **Python 3.10+**. Alternatively, open the notebook in Google Colab.
2. For local use, create a virtual environment and install dependencies:

   ```bash
   python -m venv .venv
   # On Windows:
   .venv\Scripts\activate
   # On macOS / Linux:
   # source .venv/bin/activate
   pip install -r requirements.txt
   ```

3. Get your own API key from [The Guardian Open Platform](https://open-platform.theguardian.com/).
4. Run notebook cells in order. The configuration cell will read `GUARDIAN_API_KEY` from your environment, or **ask for the key in a hidden input prompt** if it is not set. Never commit your key to GitHub.
5. The collection step writes `guardian_ai_dataset.csv` locally. It is excluded from Git to avoid publishing retrieved article text.

**Note:** The notebook includes an initial cell that installs the packages into a notebook environment. This is intended for Google Colab; local users can instead install `requirements.txt` before opening the notebook.

**Data reproducibility:** Results may differ across runs because the Guardian API response, availability, limits, and service rules can change. API access and use of article content are subject to The Guardian's terms.

## Methods

The notebook removes duplicate article URLs, handles missing text values, combines selected fields, examines article length/section/year distributions, and filters articles by word count. It applies basic normalisation, English stopword removal and lemmatisation. **NMF** is trained on TF-IDF features (10-topic and 8-topic experiments); **LDA** is trained on count-vectorised features (10 topics). The topic keywords and representative documents are examined qualitatively.

## Main findings

The original coursework analysis found that the **10-topic NMF model** yielded clearer and more readily interpreted themes than LDA for this collected corpus. Identified themes included AI and technology, international conflict, education, business and technology companies, and politics. Interpretability judgements are qualitative, not formal coherence scores.

### Reported model training times

| Model | Google Colab | Local machine |
| --- | ---: | ---: |
| NMF (10 topics) | 6.55 seconds | 0.98 seconds |
| LDA (10 topics) | 39.84 seconds | 15.26 seconds |

Values are taken from the original assessment report and notebook output; **they were not remeasured in this GitHub-ready package**. Runtime depends on hardware, data and software versions.

## Security and data use

- **Never commit an API key** to GitHub. The hard-coded API key present in the original coursework materials has been removed from this public-ready notebook and should be **revoked and regenerated** before further use.
- Do not commit `.env` files, downloaded article datasets or other private data.
- The published notebook retains model/EDA outputs but removes saved displays of article text samples. Running the notebook can recreate those outputs locally.
- Respect The Guardian Open Platform API and article-content usage terms.

## Built with

Python, pandas, NumPy, requests, scikit-learn, NLTK and Matplotlib. The original notebook was run in both Google Colab and a local Python environment.
