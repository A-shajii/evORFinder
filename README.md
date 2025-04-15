evORFinder: Computational Prediction of Small Open Reading Frames (smORFs)
Overview
evORFinder is a computational tool designed for the detection of small open reading frames (smORFs) in microbial genomes. Using Evo, a pretrained foundation model, the tool integrates a Sparse Mixture of Experts (MoE) architecture to enhance prediction accuracy by incorporating context-specific features. This project leverages Evo's high-dimensional embeddings to classify coding versus non-coding sequences with greater accuracy than existing models.

Project Title: Computational Prediction of Small Open Reading Frames Using Evo-Based Transfer Learning
Team Member
Aram Shajii

GitHub Repository Link
[Your GitHub Repository Link Here]

Data
The dataset for training the evORFinder model is a curated collection of short genomic sequences derived from microbial genomes in the human microbiome, augmented with Ribo-seq data. The sequences were labeled as coding (bona-fide smORFs) or non-coding. Each sequence was augmented with 100 base pairs of upstream and downstream flanking context to preserve regulatory information.

The dataset was preprocessed by removing incomplete sequences, filtering ambiguous nucleotides, and standardizing input lengths. It was then partitioned into training, validation, and test sets (80/10/10 split).

Data Access
If your data exceeds GitHub’s size limitations, it can be accessed via external links or datasets like NCBI Genome Database.

Folder Structure
bash
Copy
/evORFinder
  ├── /data                  # Dataset and input files
  ├── /scripts               # Python scripts for data preprocessing, model training, and evaluation
  ├── /notebooks             # Jupyter notebooks for exploratory data analysis and model demonstration
  ├── README.md              # This README file
  ├── requirements.txt       # List of dependencies for the project
Installation
To run this code, clone the repository and install the required packages using the following steps:

Clone the repository:

bash
Copy
git clone https://github.com/yourusername/evORFinder.git
cd evORFinder
Create a virtual environment and activate it:

bash
Copy
python -m venv venv
source venv/bin/activate  # On Windows, use venv\Scripts\activate
Install dependencies:

nginx
Copy
pip install -r requirements.txt
Run the model:

The project includes Jupyter notebooks with instructions for data preprocessing and model training. Run the notebook files to reproduce the figures and analysis.

Evaluation
The model was evaluated on multiple metrics:

Accuracy

Precision

Recall

F1 score

AUC (Area Under Curve)

Benchmarking results show that evORFinder outperforms the existing smORFinder model across all these metrics.

Results
Model Performance
evORFinder achieves higher classification accuracy and F1 score compared to smORFinder, demonstrating its superior ability to predict smORFs in both microbial and human pathogen datasets.

Figures
Figure 1: Evo embeddings visualized with t-SNE, showing clear separation of coding and non-coding smORFs.

Figure 2: Hyperparameter tuning results and performance comparison with other models.

Figure 3: Prediction of bona-fide smORFs in Mycobacterium tuberculosis H37Rv, highlighting the model's generalizability.

Future Work
Extending evORFinder to eukaryotic genomes, focusing on incorporating more complex regulatory signals.

Exploring additional scaling and optimization strategies for broader applicability in genome annotation tasks.
