# 📝 Text Summarizer

An end-to-end **Text Summarization** project that uses **Hugging Face Transformers** to train, fine-tune, and evaluate sequence-to-sequence models for abstractive summarization tasks.  

This project is structured for reproducibility, modularity, and easy extension to other datasets and models.  

---

## 🚀 Features

- 📚 Load and preprocess custom or benchmark datasets (e.g., SAMSum).  
- 🔧 Config-driven pipeline (YAML-based) for flexible parameter tuning.  
- 🧠 Train and fine-tune Transformer models (`BART`, `T5`, etc.).  
- 📊 Evaluation with standard metrics (ROUGE, BLEU).  
- ⚡ Supports **GPU/CPU execution**.  
- 🔄 Modular design with scripts for training, evaluation, and inference.  

---

## 📂 Project Structure

```
TextSummarizer/
│── app.py                     # Main entrypoint for running API/app
│── config/                    
│   └── config.yaml             # All configurations
│── src/textSummarizer/        
│   ├── components/             # Data preparation, model trainer, evaluation, etc.
│   ├── pipeline/               # Training / inference pipelines
│   ├── utils/                  # Helper functions
│   └── constants/              # Global constants
│── notebooks/                  # Jupyter notebooks for experimentation
│── saved_models/               # Trained models
│── requirements.txt            # Dependencies
│── README.md                   # Project documentation
```

---

## ⚙️ Installation

Clone the repository and set up your environment:

```bash
git clone https://github.com/your-username/TextSummarizer.git
cd TextSummarizer

# Create virtual environment (recommended)
python3 -m venv venv
source venv/bin/activate   # On Mac/Linux
venv\Scripts\activate      # On Windows

# Install dependencies
pip install -r requirements.txt
```

---

## ▶️ Usage

### **1. Training**

Update `config/config.yaml` with your dataset and training parameters, then run:

```bash
python app.py
```

This will:
- Load dataset  
- Preprocess text  
- Train the summarizer model  
- Save the model + tokenizer to `saved_models/`  

---

### **2. Evaluation**

Run evaluation on the trained model:

```bash
python -m src.textSummarizer.pipeline.model_evaluation
```

Results (ROUGE/BLEU scores) will be saved in the metrics file specified in config.  

---

### **3. Inference**

Generate summaries for custom text:

```python
from src.textSummarizer.pipeline.prediction import PredictPipeline

predictor = PredictPipeline(model_dir="saved_models")
summary = predictor.predict("Your long input text goes here...")
print(summary)
```

---

## 📊 Example

Input:
```
The meeting today focused on project deadlines and task allocation. 
The manager emphasized the importance of timely completion and collaboration.
```

Output:
```
The meeting covered deadlines, task distribution, and teamwork importance.
```

---