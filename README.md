
# ATLAS-GAME 🌍🕸️
### Precog Recruitment Task 2025 - Graphs Theme

This repository contains the solution for the **Precog Recruitment Task 2025** (Graphs Theme). The project analyzes the children's geography game "Atlas" using Graph Theory, Network Analysis, and Deep Learning (GNNs) to uncover winning strategies, community structures, and predictive insights.

## 📖 Project Overview

**Atlas** is a turn-based game where players name a place (Country or City) that begins with the last letter of the previously named place (e.g., *Indi**a*** ➡️ ***A**ustrali**a***).

This project models the game as a **Directed Graph** where:
- **Nodes**: Places (Countries/Cities)
- **Edges**: Directed connection from Place A to Place B if the last letter of A matches the first letter of B.

The goal is to analyze the game's complexity, mathematically determine "winning" strategies using centrality measures, and perform link prediction using Graph Neural Networks.

**Paper Reading Task**: Presentation Link: https://drive.google.com/file/d/1pxSRa_YnIbtVWhnKWI7xNUKG1M7wKGOV/view?usp=drive_link

## 📂 Directory Structure

The repository is structured as follows:

├── ATLAS_GAME.ipynb # Main Jupyter/Colab notebook containing all code (Extraction, Visualisation, Analysis)

├── Project REPORT ATLAS GAME.pdf # Report documenting the project

├── cities.csv # Cleaned dataset of major world cities

├── cities_cleaned.csv #Generated after data cleaning

├── countries.csv # Cleaned dataset of officially recognized countries

├── countries_cleaned.csv #Generated after data cleaning

└── README.md # Project documentation


## 🛠️ Dependencies & Libraries

The code requires a Python environment. The following major libraries are used:

- **NetworkX**: For graph construction, visualization, and centrality analysis.
- **PyTorch & PyTorch Geometric (PyG)**: For the Link Prediction bonus task (GNNs).
- **Pandas**: For data manipulation and reading CSVs.
- **Matplotlib & Seaborn**: For plotting graphs and heatmaps.

*Note: The first cell of the notebook automatically installs all required dependencies.*

## 🚀 How to Run the Project

This project is designed to run in a single environment (Google Colab or local Jupyter Notebook).

### Step 1: Open the Notebook
Open `ATLAS-1.ipynb` in Google Colab or your local Jupyter environment.

### Step 2: Upload Datasets
Ensure the two dataset files are available in the runtime environment:
- `cities.csv`
- `countries.csv`

**For Google Colab:** Upload these two files to the root "Files" section in the sidebar before running the code.

### Step 3: Install Dependencies
Run the **first cell** of the notebook. It contains the commands to download and set up the necessary environment libraries.

### Step 4: Execute Analysis
Run all subsequent cells sequentially to generate the graphs, analysis metrics, and GNN training results.

## 🧠 Approach & Methodology

### 1. Data Collection & Graph Construction (completed)
- Curated datasets for **Countries** and **Cities**.
- Built three distinct directed graphs:
  1. **Country Only**: Nodes = Countries.
  2. **City Only**: Nodes = Top 500 populated cities.
  3. **Combined**: Merged graph of countries and cities.
- **Edge Logic**: A directed edge exists from $U \to V$ if `U[-1] == V[0]`.

### 2. Graph Analysis (Task 1) (completed)
Used graph theory concepts to find strategic advantages:
- **Centrality Measures**: Calculated Degree, Closeness, and Betweenness centrality to find "Hub" nodes (safe starts) vs. "Trap" nodes.
- **Topological Metrics**: Analyzed Density and Diameter to understand game length and complexity.
- **Winning Strategy**: Identified "Sink" nodes or letters (like 'X' or 'Q') that act as dead ends, forcing an opponent to lose.

### 3. Community Detection (Task 2) (completed)
Applied clustering algorithms to find hidden structures in the Country graph:
- **Algorithms**: Implemented **Greedy Modularity** and **Louvain Community Detection**.
- **Insight**: Communities formed based on phonetic patterns (start/end letters) rather than geographical proximity.
- **Evaluation**: Validated quality using the Modularity Score.

### 4. Link Prediction (Task 3 Bonus) (completed)
Implemented neural networks to predict valid moves (edges) between countries:
- **Models**: Built and compared **Node2Vec** (shallow embeddings) and **Graph Convolutional Networks (GCN)** using PyTorch Geometric.
- **Features**: Engineered **52-dimensional one-hot vectors** capturing the first and last letters to represent the "physics" of the game.
- **Objective**: Conducted **unsupervised training** via edge masking and negative sampling to teach the model the rules of Atlas.
- **Evaluation**: Validated performance using **AUC (Area Under Curve)** and **Average Precision**, proving the GNN can successfully predict valid moves it hasn't seen before.



---
*Developed for Precog Recruitment Task 2025 by [Abd Raheem](https://github.com/abd-RAHEEM)*
