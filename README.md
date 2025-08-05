# Learning with StaR and FLAiR: Stabilizing and Enriching Randomized Neural Representations


This repository provides the complete codebase for the experiments presented in our study title "Learning with StaR and FLAiR: Stabilizing and Enriching Randomized Neural Representations" on enhancing the stability and performance of Randomized Neural Networks (RdNNs) using two novel frameworks:
- **StaR (Stable Representations)**: A spectral regulation framework that controls the singular value spread of random weight matrices to improve stability and generalization.
- **FLAiR (Few-step L$earning for Adaptive Initialization and Representation)**: A warm-up based mechanism that adaptively refines and freezes representations before solving output weights in closed-form.

The repository is structured to reflect both the **baseline models** and their **enhanced counterparts** under the StaR and FLAiR frameworks.

------------------------------------------------------------------------

## 📁 Repository Structure


├── StaR
│ ├── Baseline/ # Baseline implementations for RVFL, ELM, BLS, dRVFL (MATLAB + Python)
│ └── Proposed/ # StaR-enhanced versions of RVFL, ELM, BLS, dRVFL
│
├── FLAiR
│ ├── Baseline/ # Baseline implementations for RVFL, ELM, BLS, dRVFL (Python)
│ └── Proposed/ # FLAiR-enhanced versions of RVFL, ELM, BLS, dRVFL
│
├── README.md # You're here!




----------------------------------------------------------------------

⚙️Experimental Setup

All experiments for the baseline RVFL, ELM, and BLS models, along with their \textbf{StaR}-enhanced counterparts, are implemented using MATLAB R2023a and executed on a Windows 10 PC equipped with an Intel(R) Core(TM) i7-6700 CPU @ 3.40GHz (4 cores, 8 logical processors) and 16 GB RAM. The dRVFL model and its \textbf{StaR}-enhanced version, as well as all \textbf{FLAiR}-enhanced models and their corresponding baselines, are implemented in Python 3.12.7 within a Conda environment (version 24.11.3) and executed using Visual Studio Code on the same hardware configuration. Each dataset is preprocessed by normalizing the input features to have zero mean and unit variance. A $5$-fold cross-validation procedure is employed to ensure reliable and unbiased evaluation. In each fold, the dataset is split into $80\%$ training data and $20\%$ testing data. For every combination of hyperparameters, the model is trained on the training data and evaluated on the testing data across all $5$ folds. The testing accuracy is recorded for each fold. The final testing accuracy for each dataset is computed as the mean testing accuracy across the five folds, providing a robust estimate of the model's performance. Additionally, the standard deviation of testing accuracy across the folds is recorded to quantify the stability of the model.



-------------------------------------------------------------------

🔍 Hyperparameters

Hyperparameter tuning is performed using a grid search strategy to identify the optimal settings for each model. For each model, the regularization parameter (\( \lambda \)) is selected from \( \{10^i \mid i = -5, -4, \ldots, 5\} \). For RVFL and ELM, the number of hidden nodes (\( h \)) varies from \( [3:20:203] \), and six activation functions (Sigmoid (1), Sine (2), Tribas (3), Radbas (4), Tansig (5), and ReLU (6)) are evaluated. For BLS, the number of feature windows (\(q\)), the number of feature nodes in each window (\( p \)), and the number of enhancement nodes (\(r\)) are set as per \cite{10530427}, with Tansig as the activation function. For dRVFL, we adopt the same hyperparameter settings as provided in \cite{shi2021random} and evaluate three activation functions: Sigmoid (1), ReLU (2), and SELU (3). For the \textbf{StaR}-enhanced counterparts, the spectral bounds are selected by varying the upper threshold \( \sigma_{\text{high}} \) in the range \( \{0.5, 0.75, 1.0, 1.25, 1.5, 1.75, 2.0\} \), with the corresponding lower bound set as \( \sigma_{\text{low}} = 0.1 \cdot \sigma_{\text{high}} \). For the \textbf{FLAiR}-enhanced counterparts, the number of warm-up epochs is chosen from the range \( \{2, 3, \ldots, 10\} \), enabling progressive refinement of the input-to-hidden weights via lightweight adaptation. All \textbf{FLAiR} models are trained using the standard Adam optimizer \cite{kingma2017adammethodstochasticoptimization} for backpropagation during the warm-up phase. 


------------------------------------------------------------------------------


📂 Datasets

The dataset loading scripts assume that the datasets are stored in .txt format. (One can changed it as per the requirement)

Directory paths for loading datasets and saving results are clearly marked with placeholders in each script. Replace them with your local paths.
