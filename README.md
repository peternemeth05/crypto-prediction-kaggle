# 📈 DRW Crypto Market Prediction

## 👋 Intro

This is my project for the DRW Crypto Market Prediction competition on Kaggle. The challenge was to build a model that could predict short-term price movements for a crypto asset using a massive, minute-by-minute dataset spanning a full year.

This repository documents my entire process, from digging into the data for the first time to building and tuning the final predictive model.

---

## 🛠️ Tech Stack

* **Language:** Python
* **Libraries:**
    * `Pandas` & `NumPy` for data crunching.
    * `Matplotlib` & `Seaborn` for plotting and visualizations.
    * `Scikit-learn` for splitting the data correctly for time-series validation.
    * `LightGBM` as the main machine learning model.
* **Environment:** I developed this in a Kaggle Notebook.

---

## ✨ Key Points

* **Data Exploration (EDA):** I started by digging into the data to understand its structure. I looked for statistical trends, outliers, and patterns related to time.
* **Feature Engineering:** I didn't just use the data as-is. I created new, smarter features, especially time-based ones like the hour of the day and day of the week, to give my model more context.
* **Time-Series Validation:** To get an honest measure of my model's performance, I used `TimeSeriesSplit`. This made sure the model was always trained on past data and tested on future data, which is critical for time-series problems.
* **Feature Selection:** Instead of guessing which features were useful, I let the model tell me. I used LightGBM's feature importance plot to find the strongest signals and cut out the noise.
* **Hyperparameter Tuning:** I experimented with the model's settings (like its learning rate and complexity) to find the best configuration for this specific dataset.

---

## 🚀 The Process

I tackled this project in stages:

1.  **First Look:** I started by getting a feel for the dataset. I found that while the data was clean (no missing values), it had some extreme outliers, especially in trading volume.
2.  **Building a Baseline:** Before getting fancy, I built a simple model on a handful of features to get a starting score. This baseline was the benchmark I tried to beat with every new experiment.
3.  **Experimenting with Features:** I had a hunch that time was a key factor.
    * **Success:** Adding the `hour` and `dayofweek` as features gave me a solid performance boost.
    * **Failure:** My attempt to add lag and rolling window features actually made the score worse. This was a great lesson!
4.  **Smarter Feature Selection:** After the failed experiment, I used a feature importance plot to see what the model *actually* found useful. This confirmed that the time-based features were the most powerful clues.
5.  **Tuning the Model:** With a good set of features, I started tweaking the model's settings, which squeezed out a bit more performance.
6.  **Final Submission:** I trained my best model on the entire dataset and submitted my predictions to the competition.

---

## 🎓 Lessons Learned

* **More data isn't always better data.** My biggest takeaway was that adding more features can hurt if they're just noise. My score improved when I removed the complex lag features and stuck to the simple, powerful ones.
* **Time is everything in financial markets.** The `hour` and `dayofweek` were by far the most predictive features. The model needed to know *when* something was happening, not just *what* was happening.
* **Have a benchmark.** Creating a simple baseline model early on was the best decision I made. It turned the process into a series of clear, measurable experiments.
* **Validate correctly or you're flying blind.** Using `TimeSeriesSplit` was non-negotiable. Without it, I would have gotten misleading scores and wouldn't have known if my changes were actually helping.

---

## 💡 Areas for Improvement

* **Better Features:** I could engineer more advanced financial indicators to try and capture more subtle market dynamics.
* **Ensemble Models:** A common winning strategy is to combine the predictions of several different models. This is a clear next step to improve robustness.
* **Deeper Time-Series Models:** I could explore models like LSTMs that are specifically built to understand sequences and long-term patterns.
* **The Test Set Puzzle:** The top competitors discovered a major secret: the test data was shuffled out of chronological order. The ultimate improvement would be to write code to "un-shuffle" it before making predictions.

---

## ⚙️ Running the Project

1.  **Environment:** This notebook is built for the Kaggle platform. It's the easiest way to run it since the data is huge and the libraries are pre-installed.
2.  **Data:** You'll need the official dataset from the [DRW Crypto Market Prediction](https://www.kaggle.com/competitions/drw-crypto-market-prediction) page on Kaggle.
3.  **Execution:** The notebook is written to be run from top to bottom. Each cell builds on the last, walking through the entire analysis and modeling pipeline.

