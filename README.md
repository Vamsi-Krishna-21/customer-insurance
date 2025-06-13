import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import io
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import classification_report, accuracy_score, ConfusionMatrixDisplay
from sklearn.ensemble import RandomForestClassifier
from google.colab import files

def get_my_dataset():
    try:
        print(" Please upload your CSV file (it better have 'Age', 'EstimatedSalary', and 'Purchased'):")
        user_files = files.upload()
        if not user_files:
            print(" No file uploaded. Try again, buddy.")
            return None
        file_name = list(user_files.keys())[0]
        df_local = pd.read_csv(io.BytesIO(user_files[file_name]))

        required_cols = {'Age', 'EstimatedSalary', 'Purchased'}
        if not required_cols.issubset(df_local.columns):
            print(f" Missing required columns! Found columns: {df_local.columns.tolist()}")
            return None

        print("\n Dataset loaded! Here's a sneak peek:")
        print(df_local.head())
        return df_local
    except Exception as error:
        print(" Something went wrong during dataset upload:", error)
        return None

def process_data_in_my_way(df):
    try:
        features = df[['Age', 'EstimatedSalary']].copy()
        target = df['Purchased']

        missing_count = features['EstimatedSalary'].isnull().sum()
        if missing_count > 0:
            med_salary = features['EstimatedSalary'].median()
            features.loc[:, 'EstimatedSalary'] = features['EstimatedSalary'].fillna(med_salary)
            print(f" Filled {missing_count} missing salary values with median = {med_salary}")
        else:
            print(" No missing salary values. We're good to go!")
        return features, target
    except Exception as e:
        print(" Data processing hit a snag:", e)
        return None, None

def show_my_plot(dataframe):
    try:
        print(" Hold tight, plotting the data now...")
        plt.figure(figsize=(8, 5))
        sns.scatterplot(x='Age', y='EstimatedSalary', hue='Purchased', data=dataframe, palette='Set1')
        plt.title("Age vs Estimated Salary (and Purchases!)")
        plt.xlabel("Age")
        plt.ylabel("Estimated Salary")
        plt.grid(True)
        plt.show()
    except Exception as ex:
        print(" Plotting error! Details:", ex)

def main():
    df = get_my_dataset()
    if df is None:
        print(" Cannot continue without data. Exiting.")
        return

    X, y = process_data_in_my_way(df)
    if X is None or y is None:
        print(" Data processing failed. Game over.")
        return

    try:
        X_train, X_test, y_train, y_test = train_test_split(
            X, y, test_size=0.25, random_state=42
        )
        print(" Data split into training and testing sets.")
    except Exception as err:
        print(" Error during train/test split:", err)
        return

    try:
        scaler = StandardScaler()
        X_train_scaled = scaler.fit_transform(X_train)
        X_test_scaled = scaler.transform(X_test)
        print(" Features scaled successfully.")
    except Exception as err:
        print(" Scaling failed:", err)
        return

    try:
        print(" Training RandomForestClassifier... stand by...")
        rf_clf = RandomForestClassifier(n_estimators=100, random_state=42)
        rf_clf.fit(X_train_scaled, y_train)
    except Exception as err:
        print(" Model training error:", err)
        return

    try:
        y_pred = rf_clf.predict(X_test_scaled)
        acc = accuracy_score(y_test, y_pred)
        print(f"\n Model Test Accuracy: {acc:.2f}")
        print("\n Classification Report:")
        print(classification_report(y_test, y_pred))

        ConfusionMatrixDisplay.from_estimator(rf_clf, X_test_scaled, y_test, cmap="Blues")
        plt.title("Confusion Matrix")
        plt.show()
    except Exception as err:
        print(" Evaluation failed:", err)

    show_my_plot(df)

    try:
        print("\n Predicting on a few made-up customers...")
        custom_data = pd.DataFrame({
            'Age': [23, 37, 52, 48],
            'EstimatedSalary': [45000, 78000, 120000, 99000]
        })
        custom_scaled = scaler.transform(custom_data)
        custom_preds = rf_clf.predict(custom_scaled)
        for idx, row in custom_data.iterrows():
            result = " Purchased" if custom_preds[idx] == 1 else " Not Purchased"
            print(f"Age {row['Age']}, Salary {row['EstimatedSalary']}: {result}")
    except Exception as err:
        print(" Custom prediction failed:", err)

if __name__ == '__main__':
    main()
