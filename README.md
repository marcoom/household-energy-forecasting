# Household Electric Consumption Prediction Using Time Series

This repository contains all the materials developed as part of the final project for the Data Science diploma program by [MundosE](https://www.mundose.com/) in collaboration with the [National University of Córdoba (UNC)](https://www.unc.edu.ar/). All content in this repository is in Spanish.

## Project Overview
The increasing demand for electricity, especially with the rise of server farms supporting artificial intelligence models, has put considerable strain on the current energy infrastructure. The ability to predict household electric power consumption accurately is crucial to improving the efficiency of energy distribution and reducing operational costs. This project aims to develop predictive models that can help manage energy resources effectively, contributing to a more stable electric system.

Historical household electricity consumption data was utilized to conduct an exploratory data analysis (EDA) and preprocessing, followed by training and evaluating three different time-series prediction models:

- **Random Forests**
- **Prophet**
- **Feed Forward Neural Network**

The models were compared in terms of prediction accuracy, and a Gradio-based GUI was developed for testing the predictions interactively.

The dataset used for this project is: G. Hebrail and A. Berard. Individual Household Electric Power Consumption. UCI Machine Learning Repository. [Dataset]. 2006. url: https://doi.org/10.24432/C58K54.

## Repository Structure

The repository is organized as follows:

```
├── 1 - EDA y ETL
│   └── Visualización, análisis y preprocesado de datos.ipynb
├── 2 - Entrenamiento de modelos de ML
│   ├── Comparacion modelos.ipynb
│   ├── GUI Predicciones.ipynb
│   ├── Modelo Feed Forward Neural Network.ipynb
│   ├── Modelo Prophet.ipynb
│   ├── Modelo Random Forests.ipynb
│   └── random_forest_model.joblib
├── Informe
│   ├── Predicción del Consumo Eléctrico Domiciliario mediante Series Temporales.zip
│   └── Predicción_del_Consumo_Eléctrico_Domiciliario_mediante_Series_Temporales.pdf
├── Preguntas previas.md
└── Presentación.pptx
```

It is recommended to start with the report located in the **Informe** folder to gain a comprehensive understanding of the project's context, objectives, and methodologies.

The **Predicción del Consumo Eléctrico Domiciliario mediante Series Temporales.zip** file contains the source code for a LaTeX document detailing the project report.

The **Preguntas previas.md** file contains a preliminary analysis that addresses key questions related to problem identification, relevance, available data, potential analysis methods, specific objectives, research questions, tools, hypotheses, challenges, and work planning. It provides a structured approach to the project's problem-solving strategy.

The **Presentación.pptx** file contains a summary of the entire project, highlighting the main results and conclusions.

## Models
For specific details regarding the model architectures and hyperparameters, please refer to the corresponding Jupyter notebooks in the `2 - Entrenamiento de modelos de ML` folder.

## Getting Started
To reproduce the results or experiment with the models, navigate to the Jupyter notebooks provided in the respective directories.

Please note that the repository does not include deployment instructions for the Gradio GUI, but the interactive prediction GUI code can be found in the `GUI Predicciones.ipynb` file.

## Acknowledgments
This project was carried out as part of the Data Science diploma program by MundosE in collaboration with the National University of Córdoba (UNC).