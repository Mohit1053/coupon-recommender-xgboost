# 🎯 Coupon Assignment ML System

[![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)](https://python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange?logo=scikit-learn)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An intelligent machine learning system that predicts optimal coupon tiers (High, Mid, Low) for users based on their activity patterns, preferences, and market data. Built for RecycleHub's customer engagement optimization.

## ✨ Features

- 🤖 **Multi-Model Training** - Compares RandomForest, LogisticRegression, and XGBoost
- 📊 **Feature Engineering** - Advanced feature extraction from user logs and market data
- 📈 **PCA Analysis** - Dimensionality reduction with explained variance visualization
- 🔥 **Correlation Heatmaps** - Visual feature relationship analysis
- 💾 **Model Persistence** - Save and load trained models with joblib
- 📋 **Classification Reports** - Detailed accuracy metrics and confusion matrices

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- pip or conda

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/coupon-assign-ml.git
   cd coupon-assign-ml
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the training script**
   ```bash
   python assign.py
   ```

## 📁 Project Structure

```
coupon-assign-ml/
├── .github/
│   ├── workflows/
│   │   └── ci.yml
│   ├── ISSUE_TEMPLATE.md
│   └── PULL_REQUEST_TEMPLATE.md
├── src/
│   ├── assign.py              # Main training and evaluation script
│   └── generate_data.py       # Synthetic data generation
├── data/
│   ├── train_Userlog.json     # Training dataset
│   ├── test_Userlog.json      # Test dataset
│   └── final_scrap_prices.csv # Scrap item prices and margins
├── models/
│   └── coupon_classifier_model.joblib  # Saved trained model
├── notebooks/
│   └── assign_cupon.ipynb     # Jupyter notebook for exploration
├── .gitignore
├── .env.example
├── requirements.txt
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
└── README.md
```

## 🔬 How It Works

### 1. Feature Engineering

The system extracts comprehensive features from user data:

- **User Activity**: Order frequency, days since last order, account age
- **Sentiment Analysis**: User sentiment scores from feedback
- **Market Data**: Profit margins and competitor price competitiveness
- **Preferences**: Preferred scrap categories and user type encoding

### 2. Labeling Strategy

```python
def label_user(row, avg_margin):
    if row['days_since_last_order'] > 180:
        return 2  # ₹100 coupon (High)
    elif row['sentiment_score'] >= 0.9 or avg_margin >= 0.25:
        return 1  # ₹50 coupon (Mid)
    else:
        return 0  # No coupon (Low)
```

### 3. Model Selection

The system automatically:
- Trains multiple models (RandomForest, LogisticRegression, XGBoost)
- Evaluates with/without PCA dimensionality reduction
- Selects and saves the best-performing model

## 📊 Output

After running the training script, you'll see:

- Feature correlation matrix heatmap
- PCA explained variance plot
- Model accuracy comparisons
- Classification reports for each model
- Example predictions vs actual coupon tiers

## 🛠️ Configuration

### Coupon Tiers

| Tier | Value | Criteria |
|------|-------|----------|
| High | ₹100 | Inactive users (>180 days) |
| Mid | ₹50 | High sentiment or good margin |
| Low | None | Regular active users |

### Customization

Modify `assign.py` to:
- Adjust labeling logic thresholds
- Add new features from user data
- Tune model hyperparameters
- Change PCA variance threshold

## 📝 Requirements

```
pandas>=1.5.0
numpy>=1.21.0
scikit-learn>=1.0.0
matplotlib>=3.5.0
seaborn>=0.11.0
joblib>=1.1.0
xgboost>=1.6.0  # Optional, for best accuracy
```

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Your Name**

- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)

---

<p align="center">Made with ❤️ and scikit-learn</p>
