<h1 align="center">🏦 Customer Insurance Prediction</h1>

<p align="center">
Predicting insurance purchase using Machine Learning
</p>

<hr>

<h2>🚀 Overview</h2>
<p>
This project predicts whether a customer will purchase insurance based on:
</p>

<ul>
  <li><b>Age</b></li>
  <li><b>Estimated Salary</b></li>
</ul>

<p>
Instead of guessing, machine learning models are used to learn patterns and make predictions.
</p>

<hr>

<h2>🎯 Goal</h2>
<ul>
  <li>Compare different classification algorithms</li>
  <li>Identify the best-performing model</li>
  <li>Understand the impact of age and salary</li>
</ul>

<hr>

<h2>📊 Dataset</h2>

<table>
<tr><th>Feature</th><th>Description</th></tr>
<tr><td>Age</td><td>Customer age</td></tr>
<tr><td>EstimatedSalary</td><td>Income</td></tr>
<tr><td>Purchased</td><td>0 = No, 1 = Yes</td></tr>
</table>

<p>✔ Missing salary values are filled using <b>median</b></p>

<hr>

<h2>⚙️ Workflow</h2>

<pre>
Data → Preprocessing → Scaling → Training → Evaluation → Prediction
</pre>

<ul>
  <li>Data cleaning</li>
  <li>Feature scaling (StandardScaler)</li>
  <li>Train-test split (75/25)</li>
  <li>Model training and evaluation</li>
</ul>

<hr>

<h2>🤖 Models Used</h2>

<ul>
  <li>Logistic Regression</li>
  <li>KNN</li>
  <li>SVM</li>
  <li>Decision Tree</li>
  <li><b>Random Forest ⭐</b></li>
  <li>Neural Network</li>
</ul>

<hr>

<h2>📈 Evaluation Metrics</h2>

<ul>
  <li>Accuracy</li>
  <li>Precision</li>
  <li>Recall</li>
  <li>F1 Score</li>
</ul>

<p><b>Random Forest performed the best overall</b></p>

<hr>

<h2>📉 Visualization</h2>

<ul>
  <li>Scatter plot of Age vs Salary</li>
  <li>Colored by purchase decision</li>
</ul>

<hr>

<h2>🔮 Sample Predictions</h2>

<ul>
  <li>Age 30 → Salary 87,000 → Likely</li>
  <li>Age 40 → Median Salary → Unlikely</li>
  <li>Age 22 → Salary 600,000 → Likely</li>
  <li>Age 60 → High Salary → Likely</li>
</ul>

<hr>

<h2>🧠 Key Insights</h2>

<ul>
  <li>Salary has more influence than age</li>
  <li>Higher income → higher purchase probability</li>
  <li>Age alone is not a strong factor</li>
</ul>

<hr>

<h2>📚 Learnings</h2>

<ul>
  <li>Testing multiple models is important</li>
  <li>Feature scaling improves performance</li>
  <li>Random Forest works well for structured data</li>
  <li>Visualization helps in understanding trends</li>
</ul>

<hr>

<h2>🌍 Applications</h2>

<h3>Marketing</h3>
<ul>
  <li>Target potential customers</li>
  <li>Improve conversion rate</li>
</ul>

<h3>Business Strategy</h3>
<ul>
  <li>Predict customer behavior</li>
  <li>Optimize insurance plans</li>
</ul>

<hr>

<h2>🛠️ Tech Stack</h2>

<ul>
  <li>Python</li>
  <li>Pandas, NumPy</li>
  <li>Scikit-learn</li>
  <li>Matplotlib, Seaborn</li>
  <li>Google Colab</li>
</ul>

<hr>

<h2>🚀 Future Improvements</h2>

<ul>
  <li>Add more features</li>
  <li>Hyperparameter tuning</li>
  <li>Build a web app</li>
  <li>Auto-select best model</li>
</ul>

<hr>

<h2>✅ Conclusion</h2>

<p>
This project shows how simple features like age and salary can be used to build meaningful machine learning models for prediction.
</p>
