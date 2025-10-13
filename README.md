<div align="center">

# ⚛️ Quantum-Powered Portfolio Optimizer

*Navigating market complexity with quantum-inspired strategies.*

</div>

![Language](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge) ![Libraries](https://img.shields.io/badge/Libraries-OpenQAOA%20%7C%20Qiskit%20%7C%20Scikit--learn-purple?style=for-the-badge) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge) ![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

### Hi there! 👋

Welcome to the Quantum-Powered Portfolio Optimizer. This repository showcases a novel **hybrid quantum-classical workflow** designed to solve a complex asset selection problem. We tackle the challenge of scaling quantum optimization algorithms to a realistic number of assets by intelligently combining the strengths of classical machine learning and quantum-inspired computation.

---

## 📜 Table of Contents

* [The Challenge: Hitting the Scaling Wall](#the-challenge-hitting-the-scaling-wall-)
* [Our Approach: Divide, Conquer, and Combine](#our-approach-divide-conquer-and-combine-)
* [✨ Key Features](#-key-features)
* [🛠️ Technologies Used](#️-technologies-used)
* [🚀 Getting Started](#-getting-started)
* [💻 Usage: The 4-Step Workflow](#-usage-the-4-step-workflow)
* [🤝 Contributing](#-contributing)
* [📄 License](#-license)
* [📧 Contact](#-contact)

---

## The Challenge: Hitting the Scaling Wall 🧱

Portfolio optimization is a notoriously difficult combinatorial problem. The number of possible portfolios grows exponentially with the number of assets, making it impossible to check every combination. Our initial approach used a direct **QUBO (Quadratic Unconstrained Binary Optimization)** model for a subset of 15 assets, which worked perfectly.

However, when scaling to the full universe of **31 assets**, we hit a wall. The computational requirements became too large for a local machine, leading to kernel crashes and proving that a more intelligent strategy was needed.

---

## Our Approach: Divide, Conquer, and Combine 💡

Instead of trying to solve one massive 31-qubit problem, we adopted a powerful hybrid strategy that leverages the best of both worlds.

| Phase | Method | Description |
| :--- | :--- | :--- |
| **1. Divide & Cluster** | **Classical Machine Learning** | We use the **K-Means** algorithm to partition the 31 assets into 5 distinct clusters based on their core financial DNA: **risk** (`spreadDur`) and **return** (`oas`). This breaks the large problem into smaller, focused sub-problems. |
| **2. Conquer** | **Quantum-Inspired Optimization** | Each small cluster is converted into its own miniature QUBO problem. We then unleash the **Quantum Approximate Optimization Algorithm (QAOA)**, via the `OpenQAOA` library, on each cluster to find the "champion" assets within that group. These small simulations run quickly and efficiently on a local machine. |
| **3. Combine** | **Classical Selection** | Finally, we gather the "champions" from all the quantum runs into a single elite candidate pool. A simple and efficient classical algorithm then selects the final 10-bond portfolio from this group, ensuring a balanced and high-quality result. |

This hybrid workflow allows us to find a high-quality, near-optimal solution without requiring a large-scale quantum computer or a supercomputer.

---

## ✨ Key Features

- **Hybrid Quantum-Classical Architecture:** Combines classical ML for pre-processing and quantum algorithms for core optimization.
- **Scalable by Design:** Overcomes the limitations of small-scale simulators by decomposing a large problem (31 assets) into smaller, solvable pieces (5-9 assets each).
- **Data-Driven Clustering:** Uses Scikit-learn's K-Means to create financially relevant asset groups automatically.
- **Automated End-to-End Workflow:** Scripts are numbered and designed to be run sequentially for a seamless user experience.
- **Insightful Visualization:** Generates a final risk-return plot to evaluate the performance of the resulting portfolio.

---

## 🛠️ Technologies Used

This project is built on a foundation of powerful open-source libraries:

- **Quantum Computing:**
  - `OpenQAOA`: A high-level library for creating and running quantum/classical hybrid optimization algorithms.
  - `Qiskit`: The foundational framework for quantum computing in Python.
- **Machine Learning & Data Science:**
  - `Pandas`: For data manipulation and analysis of the `assets.csv` file.
  - `NumPy`: For efficient numerical operations and QUBO matrix construction.
  - `Scikit-learn`: For implementing the K-Means clustering algorithm.
- **Visualization:**
  - `Matplotlib`: For creating the final risk-return scatter plot.

---

## 🚀 Getting Started

Follow these steps to get the project running on your local machine.

### Prerequisites

- Python 3.8 or higher

### 1. Clone the Repository

git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name 

2. Install Dependencies
All required libraries are listed in the requirements.txt file.

Bash

pip install -r requirements.txt
💻 Usage: The 4-Step Workflow
The project is designed to be run as a sequence of scripts. Execute them from your terminal in the following order.

Step 1: Create the Asset Clusters
This script performs K-Means clustering to divide the 31 assets into 5 groups.

Bash

python 01_classical_clustering.py
Step 2: Generate QUBOs for All Clusters
This script automatically creates a unique QUBO model for each of the 5 clusters.

Bash

python 03_generate_all_qubos.py
Step 3: Solve the QUBOs with OpenQAOA
This is the quantum step. It will solve each of the 5 small QUBO problems locally.

Bash

python 05_solve_all_clusters_local.py
Step 4: Assemble and Visualize the Final Portfolio
This script collects the results from the quantum runs, builds the final portfolio, and generates the risk-return plot.

Bash

python 06_assemble_and_visualize.py
After the final step, a plot named hybrid_risk_return_plot.png will be saved in your project directory.

🤝 Contributing
Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

Fork the Project

Create your Feature Branch (git checkout -b feature/AmazingFeature)

Commit your Changes (git commit -m 'Add some AmazingFeature')

Push to the Branch (git push origin feature/AmazingFeature)

Open a Pull Request

Please open an issue first to discuss what you would like to change.

📄 License
This project is distributed under the MIT License. See the LICENSE file for more information.
