Cyber Threat Intelligence Sentence Classification — Bachelor's Thesis
Author: Hugo Becerra Fernández
Institution: Universidad Carlos III de Madrid (UC3M)
Degree: BSc in Computer Engineering · 2026
Thesis grade: 9.2/10
Repository: TFG-HUGO-BECERRA
Overview
This repository contains the research code, datasets and thesis report for my Bachelor's Thesis, “Evaluación de modelos de PLN para detección de amenazas en ciberseguridad” (Evaluation of Natural Language Processing Models for Cybersecurity Threat Detection).

The project investigates sentence-level binary classification of cybersecurity threat intelligence (CTI) reports: determining whether a sentence is relevant to characterising malware or is not relevant. The goal is to study whether classical machine learning, neural networks and transformer-based language models can support analysts who must review large volumes of technical threat reporting.

The experiments are based on SemEval-2018 Task 8, Subtask 1, using malware-related text classification data. This is a research and experimentation repository, not a production detection engine.
Research questions
- How do traditional feature-based classifiers compare with neural and transformer-based models on specialised CTI language?
- Does security-domain pretraining provide an advantage over general-purpose language models?
- Can data augmentation improve recognition of the minority relevant class?
- How effective are zero-shot and few-shot approaches without task-specific supervised training?
Approaches investigated
Family	Experiments and methods
Classical machine learning	TF-IDF features, Linear Support Vector Classification (LinearSVC), hyperparameter search
Recurrent neural networks	Bidirectional Long Short-Term Memory (BiLSTM) with attention; replication and comparison of earlier approaches
General-purpose transformers	BERT, RoBERTa and DeBERTa fine-tuning
Security-oriented transformers	CTI-BERT, SecureBERT and SecBERT experiments
Data augmentation	Back-translation and minority-class expansion
Prompt-based methods	Zero-shot and few-shot classification with generative / natural language inference models


The main evaluation measure is F1 for the malware-relevant class, because the classes are imbalanced and overall accuracy can obscure performance on relevant sentences.
Selected results
The following scores summarise experiments reported in the thesis; they are not benchmark claims for production deployments.
Experiment	F1 (relevant class)
BiLSTM with attention — reproduced configuration	0.5673
SecureBERT 2.0	0.5515
BERT with back-translation augmentation	0.5382
RoBERTa base	0.5323
Optimised TF-IDF + LinearSVC	0.5271
BERT base	0.5230
DeBERTa base	0.5193
CTI-BERT	0.5147


These are representative results from the experiments documented in the accompanying thesis. Comparisons should be interpreted alongside the dataset versions, training configurations, evaluation protocol and stated limitations.
Repository structure
.
├── Evaluación de modelos de PLN para detección de amenazas en ciberseguridad.pdf
├── data/
│   └── subtask1/
│       ├── train.csv
│       ├── dev.csv
│       └── test.csv
└── subtask1/
    ├── BASELINE_ORIGINAL.ipynb
    ├── busqueda_hiperparametros_SVM.ipynb
    ├── PREPARACION_DATOS_2.0.ipynb
    ├── Modelo_Villani.ipynb
    ├── Replicacion_Villani.ipynb
    ├── Fine_Tuning_multimodelo.ipynb
    ├── BERT_ConfigA_BERT_BT.ipynb
    ├── secure_bert_original+backtranslation.ipynb
    ├── PROMPTING_Y_GENERATIVOS.ipynb
    ├── Generación_figuras.ipynb
    ├── TAREA_OCW.ipynb
    ├── TAREA_V2.0.ipynb
    ├── [DESCARTADO]BERT+BERT_BACKSTRANSLATION.ipynb
    ├── ideas_descartadas.ipynb
    └── notebook-preparaci-n-datos.ipynb
Notebook guide
- Data processing: PREPARACION_DATOS_2.0.ipynb, notebook-preparaci-n-datos.ipynb.
- Classical baselines: BASELINE_ORIGINAL.ipynb, busqueda_hiperparametros_SVM.ipynb.
- BiLSTM / attention: Modelo_Villani.ipynb, Replicacion_Villani.ipynb.
- Transformer fine-tuning: Fine_Tuning_multimodelo.ipynb, BERT_ConfigA_BERT_BT.ipynb, secure_bert_original+backtranslation.ipynb.
- Prompt-based experimentation: PROMPTING_Y_GENERATIVOS.ipynb.
- Figures and exploratory variants: Generación_figuras.ipynb, TAREA_OCW.ipynb, TAREA_V2.0.ipynb, and notebooks marked as discarded/ideas.
The full methodology, experimental setups, findings and limitations are described in the PDF thesis report at the repository root.
Running the experiments
The notebooks were developed primarily for Jupyter / Google Colab. They are independent experiments rather than a single command-line application, and some assume Colab-specific paths, external datasets, pretrained model downloads or additional resources.
1. Open the notebook relevant to the experiment you want to inspect or reproduce.
2. Use a Python 3 environment with Jupyter or Google Colab. Install the libraries imported by that notebook; depending on the experiment, these include numpy, pandas, scikit-learn, matplotlib, tensorflow, torch, transformers, datasets, huggingface_hub, accelerate, evaluate and imbalanced-learn.
3. Check the dataset paths and configuration inside the notebook. Some experiments load the public Hugging Face dataset namespace hugobecerra/DATASET3.0 and reference a split named test_1.csv, whereas the files included under data/subtask1/ use test.csv.
4. Adjust file paths and any authentication configuration for your own environment; do not use historical credentials contained in an experiment notebook.
5. Run cells in order and compare results with the thesis, accounting for random seeds, hardware, library versions and computational limits.
Reproducibility note: The repository currently does not provide a pinned dependency lockfile or an end-to-end automated reproduction script. Some models require GPU memory, external downloads or embeddings. Exact numerical reproduction is therefore not guaranteed without recreating the experiment-specific environment.
Limitations
- Strong class imbalance makes the F1 score of the relevant class more informative than accuracy alone.
- Limited compute resources restricted the number of seeds, training runs and parameter configurations.
- Dataset and model sensitivity: Results depend on the train/development/test variants and exact evaluation procedures.
- Research scope: This is sentence classification for CTI analysis, not malware execution, exploit development, incident containment or vulnerability patching.
Technologies
Python · Jupyter Notebook · scikit-learn · TensorFlow/Keras · PyTorch · Hugging Face Transformers / Datasets · pandas · NumPy · NLP · Experimental model evaluation.
Project status and use
This repository is public to make the thesis methodology and experimental code inspectable. No explicit software licence is currently included. Public visibility by itself does not grant redistribution or modification rights. Dataset and pretrained-model assets remain subject to the terms of their respective sources.

For academic interpretation, please consult the thesis PDF and cite the relevant original datasets, architectures and research publications described there.
