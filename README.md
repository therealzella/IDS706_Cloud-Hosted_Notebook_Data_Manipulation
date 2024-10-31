# Cloud-Hosted Notebook Data Manipulation

## Project Overview
This project showcases data manipulation techniques on a dataset of various cereal brands (`cereal.csv`). The analysis involves loading the dataset from a cloud-hosted Jupyter Notebook, performing data cleaning, and applying feature engineering to derive new insights. The notebook is hosted on Google Colab for ease of access and reproducibility.

This project also includes a CI/CD pipeline set up with GitHub Actions for code quality checks and automated testing, ensuring that all scripts are error-free and conform to Python standards.

## Dataset
The dataset (`cereal.csv`) contains information about various cereal brands, including attributes like:
- **Calories**: The calorie content per serving.
- **Protein**: Protein content per serving.
- **Fiber**: Fiber content per serving.
- **Sugars**: Sugar content per serving.
- **Manufacturer**: Company that produces the cereal.

### Dataset Source
The dataset is part of the project repository, and it’s directly loaded from GitHub within the Google Colab notebook.

## Notebook Access
You can view and run the notebook on Google Colab:
- [Cloud-Hosted Notebook on Google Colab](https://colab.research.google.com/drive/1ra8Ig0mdAQJ2HZeTVXzqt7cW9nlSYSnN?usp=sharing)

## Data Manipulation Tasks
The notebook performs the following data manipulation tasks:

### 1. Data Loading
- **Source**: Loads the `cereal.csv` file from the GitHub repository using the raw file URL.
- **Code Example**:
  ```python
  import pandas as pd
  url = 'https://raw.githubusercontent.com/therealzella/IDS706_Cloud-Hosted_Notebook_Data_Manipulation/main/cereal.csv'
  df = pd.read_csv(url)

### 2. Data Cleaning
- **Remove Duplicates**: Ensures unique entries by dropping duplicate rows.
- **Handle Missing Values**: Fills any missing values with default values to avoid errors in analysis.

### 3. Feature Engineering
- **Calorie Category**: Categorizes cereals based on calorie content:
  - Low (<100 calories), Medium (100-150 calories), High (>150 calories).
  - Utilizes numpy.select to create a new column calorie_category.
  - Code Example:
    import numpy as np
    conditions = [
        (df['calories'] < 100),
        (df['calories'] >= 100) & (df['calories'] < 150),
        (df['calories'] >= 150)
    ]
    choices = ['Low', 'Medium', 'High']
    df['calorie_category'] = np.select(conditions, choices, default='Unknown')
  - Sugar-to-Fiber Ratio: Adds a column sugar_fiber_ratio to measure the balance between sugar and fiber in each cereal.

### 4. Aggregation and Filtering
- **Manufacturer Analysis**: Groups data by manufacturer to calculate average calories, protein, and fiber content for each brand.
- **Filtering for High Protein**: Filters cereals with more than 4 grams of protein per serving.

### 5. Insights
Summary: The final section of the notebook summarizes findings, such as the calorie distribution across different manufacturers, high protein cereals, and cereals with favorable sugar-to-fiber ratios.

### CI/CD Pipeline

The project includes a GitHub Actions workflow for continuous integration and testing.

- **CI/CD Setup**
The workflow, defined in .github/workflows/ci.yml, includes the following steps:

- Dependency Installation: Installs all required libraries from requirements.txt.
- Code Linting: Uses flake8 to ensure code adheres to Python style standards.
- Automated Testing: Runs pytest to execute any unit tests included in the repository.
- Notebook Execution (Optional): Converts the notebook to a Python script and runs it to validate all cells execute without errors.

**Running the Workflow Locally**
You can replicate the CI/CD pipeline steps locally with:

```
bash
Copy code
pip install -r requirements.txt
flake8 .  # Linting
pytest    # Testing
Requirements
```

To run the notebook or the CI/CD pipeline, you’ll need the following libraries:

pandas: For data manipulation.
numpy: For numerical operations and creating conditions.
jupytext (if converting the notebook to a script): For converting .ipynb files to .py.
flake8: For code linting.
pytest: For testing.

Install these dependencies with:

bash
Copy code
pip install -r requirements.txt
Usage Instructions

View Notebook on Colab: Click the Colab link to view and run the notebook interactively.

Run Locally:

Clone the repository:
bash
Copy code
git clone https://github.com/your-username/your-repo.git
Install dependencies:
bash
Copy code
pip install -r requirements.txt

Open the notebook in Jupyter Notebook or JupyterLab.

Run CI/CD Pipeline: The GitHub Actions workflow is configured to run automatically on each push or pull request. To trigger it, push any change to the repository.
Key Insights and Findings

Calorie Distribution: Most cereals fall into the Low calorie category, with fewer options in the High category.
High Protein Cereals: A select few cereals offer more than 4 grams of protein, which might appeal to health-conscious consumers.
Sugar-to-Fiber Balance: Cereals with a favorable sugar-to-fiber ratio are highlighted, providing insights into healthier options.
Troubleshooting

If you encounter issues running the notebook or the CI/CD pipeline, consider the following:

ModuleNotFoundError: Ensure all dependencies are installed by running pip install -r requirements.txt.
CI/CD Failures: Check the GitHub Actions logs to identify where the error occurs, such as linting or notebook execution.
