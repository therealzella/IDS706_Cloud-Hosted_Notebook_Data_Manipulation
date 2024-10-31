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

