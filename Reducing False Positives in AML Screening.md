## Reducing False Positives in AML Screening Using Data Science!
---

If a sanctions screening system was generating an excessive number of false positives, resulting in operational delays and unnecessary customer friction. To address this, combining feature engineering, rule tuning, and statistical evaluation would likely reduce the false positive rate while maintaining true positive performance.

a solution:

- Analyze historical alert data using SQL and Python to identify recurring false positive patterns.

- Engineer new features such as customer_risk_score and transaction_frequency to contextualize screening matches.

- Tune the match thresholds in Firco Continuity based on ROC analysis
Implemented mitigation logic for low-risk, high-frequency flagged entities.

- Conduct A/B testing with a holdout set to ensure no loss in true positive rates.

Inspired by how organizations like PayPal are investing in scalable, intelligent AML screening models.

Below is a simplified example of how I used IsolationForest to identify anomalies in match behavior:

```python

from sklearn.ensemble import IsolationForest
import pandas as pd

# Load preprocessed features
df = pd.read_csv('screening_features.csv')
features = df[['match_score', 'customer_risk_score', 'txn_frequency']]

# Fit anomaly model
model = IsolationForest(contamination=0.1, random_state=42)
df['anomaly_flag'] = model.fit_predict(features)

# Flag likely false positives
likely_false_positives = df[df['anomaly_flag'] == 1]

```
