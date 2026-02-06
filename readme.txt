
CARBON-AWARE IMAGE CLASSIFICATION WITH ACO (CIFAR-100)

This project implements a "Green AI" approach to image classification using the CIFAR-100 dataset. It utilizes Ant Colony Optimization (ACO) to automate hyperparameter tuning and model selection, specifically optimizing for a balance between Test Accuracy and Carbon Emissions (CO2).

The system evaluates both Deep Learning (ResNet-18) and Classical Machine Learning models (SVM, XGBoost, etc.) using a two-stage ACO process.

KEY FEATURES

* Carbon Tracking: Integrated with CodeCarbon to measure real-time CO2 emissions (kg) for every training run.
* Hybrid Modeling:
* Deep Learning: Fine-tuned ResNet-18 (with Automatic Mixed Precision).
* Classical ML: SVM, Random Forest, XGBoost, kNN, and Logistic Regression trained on PCA-reduced ResNet-18 embeddings.


* Ant Colony Optimization (ACO):
* Intra-Algorithm ACO: Swarm-based search for the best hyperparameters within each algorithm type.
* Inter-Algorithm ACO: High-level selection to identify the best overall model across all types.


* Dataset: CIFAR-100 (20k "fast train" split for efficiency).

METHODOLOGY

1. Feature Extraction: Images are passed through a pre-trained ResNet-18 (ImageNet weights) to generate embeddings, which are reduced to 100 dimensions using PCA.
2. Search Space: The ACO algorithm explores a defined grid of hyperparameters (e.g., Learning Rate, Batch Size for ResNet; C, Gamma for SVM; n_estimators for Random Forest).
3. Optimization Function: The "pheromone" deposit in ACO is calculated based on a weighted combination of Validation Accuracy and CO2 Emissions.
4. Selection: The system outputs a "Champion" model that offers the best trade-off.


RESULTS STRUCTURE

The simulation generates a table comparing the best configuration found for each algorithm. Example columns include:

* Algorithm (e.g., ResNet18, SVM_RBF)
* Validation Accuracy
* Test Accuracy
* CO2 (kg)
* Hyperparameters

