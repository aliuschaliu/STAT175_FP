# STAT175_FP

This repository contains the code for our STAT 175 final project, **When Do Graph Attention Networks Help? A Comparative Study on Twitch Gamer Networks**. The project compares graph neural network models on six Twitch language-region graphs and adds a GAT cross-graph transfer experiment.

## Repository Structure

- `175FP_MLP.ipynb`  
  Trains and evaluates the feature-only MLP baseline.

- `175FP_GCN.ipynb`  
  Trains and evaluates the Graph Convolutional Network baseline.

- `175FP_GraphSAGE.ipynb`  
  Trains and evaluates the GraphSAGE baseline.

- `175FP_GAT.ipynb`  
  Trains and evaluates the Graph Attention Network model.

- `175FP_H2GCN.ipynb`  
  Trains and evaluates the H2GCN model.

- `175FP_Transfer.ipynb`  
  Runs the GAT cross-graph transfer task. For each ordered source-target pair of Twitch graphs, it trains GAT on the source graph and evaluates directly on the target graph.

- `mainmodels_macro-f1_comparison.ipynb`  
  Aggregates saved model results and produces the main macro-F1 comparison plots.

## Datasets

The experiments use six Twitch language-region graphs:

`DE`, `EN`, `ES`, `FR`, `PT`, and `RU`.

Each graph contains Twitch users as nodes, followership links as edges, sparse binary node features, and a binary mature-content label.

## Experimental Protocol

All within-graph experiments use:

- stratified `60/20/20` train/validation/test splits,
- five random seeds: `0, 1, 2, 3, 4`,
- shared splits across models for fair comparison,
- early stopping based on validation performance,
- test reporting using macro-F1, accuracy, and ROC-AUC.

The transfer experiment uses GAT only. It trains on one language graph and evaluates on another without using target training labels.

## Reproducibility

Each notebook saves or reads the train/validation/test split files so that models are evaluated on identical splits. Result files and figures are generated from the notebook outputs and used in the final report.

## Main Result

GAT is not uniformly best on the Twitch graphs. GCN achieves the strongest average within-graph macro-F1, while GAT is more competitive on some graphs and shows source- and target-dependent transfer behavior across language regions.
