
# evORFinder: Computational Prediction of Small Open Reading Frames Using Evo-Based Transfer Learning

## Overview

**evORFinder** is a computational pipeline designed to predict small open reading frames (smORFs) in genomic sequences by leveraging Evo, a large foundation model pre-trained on over 80,000 bacterial, archaeal, and bacteriophage genomes. By utilizing Evo's high-dimensional embeddings, evORFinder employs a Sparse Mixture of Experts (MoE) architecture to classify coding and non-coding sequences with high accuracy. The model outperforms traditional approaches like smORFinder in both sensitivity and specificity, making it a valuable tool for discovering previously unannotated genomic regions.

This repository contains all the code and data necessary to reproduce the key figure from the evORFinder study, showcasing model performance and accuracy convergence over training epochs.

## Data

The dataset used to train the model contains genomic sequences from bacterial species within the human microbiome, as well as sequences curated from *Mycobacterium tuberculosis* (Mtb) H37Rv for biological validation. Sequences were annotated as either coding (bona-fide smORFs) or non-coding. The data was preprocessed by removing incomplete sequences, filtering ambiguous nucleotides, and standardizing input lengths. A subset of 10,000 entries was used for training, validation, and testing.

Since the dataset may be too large to upload directly, access the curated dataset from the following locations:
- [Mtb H37Rv Genome Data](https://www.ncbi.nlm.nih.gov/nuccore/448814763)
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

### Generate Visualizations
After training, generate the figures for your report using:
```
python code/evORFinder.py --generate_figures
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

