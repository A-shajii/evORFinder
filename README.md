
# evORFinder: Computational Prediction of Small Open Reading Frames Using Evo-Based Transfer Learning

## Overview

**evORFinder** is a computational pipeline designed to predict small open reading frames (smORFs) in genomic sequences by leveraging Evo, a large foundation model pre-trained on over 80,000 bacterial, archaeal, and bacteriophage genomes. By utilizing Evo's high-dimensional embeddings, evORFinder employs a Sparse Mixture of Experts (MoE) architecture to classify coding and non-coding sequences with high accuracy. The model outperforms traditional approaches like smORFinder in both sensitivity and specificity, making it a valuable tool for discovering previously unannotated genomic regions.

This repository contains all the code and data necessary to reproduce the key figure from the evORFinder study, showcasing model performance and accuracy convergence over training epochs.

## Data

The dataset used to train the model contains genomic sequences from bacterial species within the human microbiome, as well as sequences curated from *Mycobacterium tuberculosis* (Mtb) H37Rv for biological validation. Sequences were annotated as either coding (bona-fide smORFs) or non-coding. The data was preprocessed by removing incomplete sequences, filtering ambiguous nucleotides, and standardizing input lengths. A subset of 10,000 entries was used for training, validation, and testing.

Since the dataset may be too large to upload directly, access the curated dataset from the following locations:

Curated Bacterial Genome Dataset from Human Microbiome: 
- Sberro, H., Fremin, B. J., Zlitni, S., Edfors, F., Greenfield, N., Snyder, M. P., ... & Bhatt, A. S. (2019). Large-scale analyses of human microbiomes reveal thousands of small, novel genes. Cell, 178(5), 1245-1259. DOI: 10.1016/j.cell.2019.07.019

Mycobacterium tuberculosis (Mtb) H37Rv smORF Dataset:
- [Mtb H37Rv Genome Data](https://www.ncbi.nlm.nih.gov/nuccore/448814763)


Biological Validation/Ribo-seq Data Set:
- [Ribo-seq Data](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE129355)

## Folder Structure

```
evORFinder/
├── data/
│   └── raw_data/         # Raw dataset and sequence annotations links 
├── code/
│   ├── evORFinder.py     # Main pipeline script
├── results/
│   ├── figures/          # Generated figures for the report
├── README.md             # This file
```

## Installation

### Prerequisites

- Python 3.7+
- PyTorch 1.10+ (recommended)
- Evo (available at [Evo GitHub repository](https://github.com/facebookresearch/Evo))

To run the analysis, you will need to install the required dependencies. These include libraries for data handling, machine learning, and deep learning. You can install them using pip.

Dependencies:

evo: Evo pre-trained embeddings

torch: PyTorch for deep learning

matplotlib: For data visualization

pandas: Data handling

numpy: Numerical operations

scikit-learn: For metrics, cross-validation, and other machine learning tools

scipy: For scientific computations (optimization, stats, etc.)

tqdm: Progress bar for loops

seaborn: For statistical visualizations

biopython: For bioinformatics 

You can install all dependencies with the following command:

pip install evo==0.1.3 torch==1.13.1 matplotlib==3.7.0 pandas==1.5.3 numpy==1.24.0 scikit-learn==1.2.0 scipy==1.10.0 tqdm==4.64.1 seaborn==0.11.2 biopython==1.81


### Setup Instructions

1. **Clone this repository:**
   ```
   git clone https://github.com/yourusername/evORFinder.git
   cd evORFinder
   ```

2. **Create a virtual environment:**
   ```
   python3 -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scriptsctivate`
   ```

3. **Install the required dependencies:**
  -Listed above 

4. **Download the dataset:**
   - Follow the provided links to download the raw data and place it in the `data/raw_data/` directory.

5. **Run the model:**
   - To start training the model, use the following code:
     ```
     python code/evORFinder.py
     ```

6. **Generate Figures:**
   - Once training is complete, the figures from the results will be genereated with the same code: 
     ```
     python code/evORFinder.py 
     ```

## Usage

### Training the Model
To train the model on the dataset, use the command:
```
python code/evORFinder.py --train --epochs 100 --batch_size 32
```
Adjust the number of epochs and batch size according to your computational resources.

### Evaluation
To evaluate the trained model on the test set, use the command:
```
python code/evORFinder.py --evaluate --checkpoint <path_to_checkpoint>
```

## Results

Figure 2 in this repository demonstrates the following:

1. **(A) Model Performance Comparison:**  
   evORFinder significantly outperforms all other models tested, including smORFinder and a Sparse MoE model using 4-mer embeddings. Performance metrics include accuracy, precision, recall, F1 score, and AUC.

2. **(B) Accuracy Convergence Over Epochs:**  
   The training and validation accuracy show that evORFinder continues to improve without signs of overfitting, even after 100 epochs. This suggests potential for further optimization with more computational resources.

## References

- Kute, P. M., Soukarieh, O., Tjeldnes, H., Trégouët, D.-A., & Valen, E. (2022). Small Open Reading Frames, How to Find Them and Determine Their Function. *Frontiers in Genetics, 12*.
- Nguyen, E. et al. (2024). Sequence modeling and design from molecular to genome scale with Evo. *Science, 386*, eado9336.

