# 🇫🇷 French CEFR Readability Analyzer (Flask API)

This project is a language-aware readability analyzer for French text. It estimates readability and CEFR level (A1–C2) using real-world linguistic resources. Designed as a lightweight MCP server, it runs as a Flask API directly from a Jupyter notebook — ideal for fast testing and educational applications.

## 🚀 Features

- Calculates French Flesch-style readability score
- Detects CEFR vocabulary level of each word using the FLELex corpus
- Returns CEFR-level distribution and highlights complex words
- Flask API runs directly inside Jupyter — no setup, just POST and play

## 📂 Folder Structure

french-cefr-analyzer/
├── server_notebook.ipynb     # Jupyter notebook with Flask API
├── FLELex_TreeTagger.csv     # CEFR word list with frequency distribution
├── requirements.txt          # Python dependencies
└── README.md                 # You're reading it

## 🧪 Sample Input

Send a POST request to `/analyze` with:

{
  "text": "Le chat noir dort sur le canapé. Il rêve de poissons frais."
}

## 📤 Sample Output

{
  "readability": {
    "word_count": 12,
    "sentence_count": 2,
    "syllable_count": 15,
    "flesch_score": 108.91,
    "complex_words": ["canapé"]
  },
  "cefr": {
    "word_levels": {
      "le": "A1",
      "chat": "A1",
      ...
    },
    "cefr_distribution": {
      "A1": 5,
      "A2": 2,
      "B1": 2,
      ...
    },
    "estimated_cefr_level": "A1"
  }
}

## 🧰 Setup Instructions

1. Install dependencies:
   pip install -r requirements.txt
   python -m spacy download fr_core_news_sm

2. Launch the Jupyter notebook `server_notebook.ipynb`

3. Run the cell to start the Flask server

4. Send a POST request to:
   http://127.0.0.1:5000/analyze

## 📚 Data Source

Vocabulary CEFR levels are sourced from the FLELex TreeTagger corpus, built by the CEFRLex project at Université catholique de Louvain. These reflect word distributions across levels A1–C2 from French learner corpora.

## ✨ Author

Built by Venkata Gade, with the goal of bridging NLP and language pedagogy.

This API is part of a larger project — **Aaron**, an intelligent language learning app I’m building that offers CEFR-aligned reading materials, grammar-aware feedback, and personalized vocabulary tracking.

If you found this useful, feel free to ⭐ star, 🍴 fork, or 🙌 share!