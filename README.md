URL Classification Ensemble

This project focuses on detecting and categorizing deceptive or phishing URLs using an ensemble of machine learning models. It combines CatBoost, XGBoost, and LightGBM to improve accuracy and robustness against adversarial domain obfuscation techniques.

Misclassification Analysis

We manually reviewed 500 misclassified samples to better understand common error types:

Short deceptive domains — e.g., paypa1-login.com

Highly obfuscated links — involving nested redirects or encoded parameters

Brand-impersonation URLs — mimicking popular domains with subtle character changes

Error Breakdown
Error Type	Percentage	Description
Borderline lexical cases	61%	Ambiguous lexical patterns near decision boundaries
Novel subdomain structures	24%	Unseen or creative subdomain layouts
Short benign URLs	15%	Legitimate short links incorrectly flagged

Insight:
These findings highlight opportunities to enhance the model with selective metadata augmentation, such as integrating WHOIS or DNS-based features for better generalization.

Ablation Study

To assess each component’s contribution, we performed an ablation study by removing one base learner at a time and re-evaluating performance.

Model Variant	Accuracy	Recall	F1 Score
Full Ensemble	95.96%	0.954	0.958
No CatBoost	95.2%	0.947	0.951
No XGBoost	95.3%	0.948	0.952
No LightGBM	93.89%	0.932	0.937

Conclusion:
The ensemble model achieved the best balance across all metrics. Notably, LightGBM contributed significantly to overall performance, indicating its importance in capturing complex URL patterns.

🚀 Future Work

Introduce metadata-based augmentation to capture contextual signals.

Explore transformer-based embeddings for domain-level representation.

Implement online learning to adapt to evolving phishing strategies.

🧠 Tech Stack

Python 3.10+

CatBoost

XGBoost

LightGBM

scikit-learn

pandas, numpy, matplotlib

📁 Project Structure
project/
│
├── data/
│   ├── train.csv
│   ├── test.csv
│
├── models/
│   ├── ensemble.py
│   ├── catboost_model.py
│   ├── xgboost_model.py
│   ├── lightgbm_model.py
│
├── notebooks/
│   └── analysis.ipynb
│
├── results/
│   ├── ablation_results.csv
│   └── misclassifications.json
│
├── README.md
└── requirements.txt



Usage
python models/ensemble.py --train data/train.csv --test data/test.csv


Results and logs will be saved in the results/ directory.


If you use this project in your research, please cite:

@misc{urlensemble2025,
  author = {Your Name},
  title = {URL Classification Ensemble for Phishing Detection},
  year = {2025},
  howpublished = {\url{https://github.com/yourusername/url-ensemble}}
}