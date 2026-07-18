# Quora Question Pairs - Duplicate Detection

An end-to-end Natural Language Processing (NLP) pipeline designed to identify semantic similarities and flag duplicate question pairs. By extracting deep text characteristics and utilizing ensemble machine learning models, this system can predict whether two completely different sentence structures convey the same underlying intent.

## 📊 Dataset Context
The model is trained on a subset of the official Quora Question Pairs dataset. Due to GitHub's file size limits, the raw datasets are omitted from this repository via `.gitignore`.
* **Data Source:** [Kaggle Quora Question Pairs Competition](https://www.kaggle.com/c/quora-question-pairs/data)
* **Training Subset size:** 30,000 rows

---

## 🛠️ Feature Engineering Pipeline

The system engineers 15+ advanced text and length features across three primary categories to maximize predictive accuracy:

### 1. Token Features (`fetch_token_features`)
* **cwc_min / cwc_max:** Ratio of common non-stopwords relative to the length of the shorter/longer question.
* **csc_min / csc_max:** Ratio of common stopwords relative to the length of the shorter/longer question.
* **ctc_min / ctc_max:** Ratio of total common tokens across both questions.
* **first_word_eq / last_word_eq:** Binary indicators flagging whether the sentences begin or end with identical tokens.

### 2. Length Features (`fetch_length_features`)
* **abs_len_diff:** Absolute difference between the token counts of both questions.
* **avg_tk_len:** Average token length across both questions.
* **longest_substr_ratio:** Length ratio of the absolute longest common substring using optimized `SequenceMatcher` indexing.

### 3. Fuzzy String Ratios (`fetch_fuzzy_features`)
* **fuzz_ratio & fuzz_partial_ratio:** Core Levenshtein alignment metrics across raw and windowed text formats.
* **token_sort_ratio & token_set_ratio:** Ratios calculated after sorting and deduplicating tokens, ensuring order variations don't break the model.

---

## 🚀 Getting Started

### Prerequisites
Make sure you have Python 3.8+ installed. 

### Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
   cd your-repo-name
