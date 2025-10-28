🧠 Text-to-SQL LLM Fine-Tuning

🔍 Natural Language to SQL Query Generation using Fine-Tuned Large Language Models (LLMs)

📘 Project Overview

This project demonstrates how large language models — Mistral-7B, LLaMA-3-8B, and Phi-3-mini — can be fine-tuned using LoRA (Low-Rank Adaptation) to translate natural language questions into SQL queries.
Our pipeline enables efficient fine-tuning even on modest hardware, producing syntactically valid and semantically accurate SQL outputs.

✅ Goal: Enable users to query databases in plain English — no SQL expertise required.

🚀 Key Contributions

Fine-tuned 3 state-of-the-art LLMs — Mistral-7B, LLaMA-3-8B, Phi-3-mini — using LoRA for efficient parameter tuning.

Built a modular pipeline for:

Environment setup, data loading, and prompt formatting

Fine-tuning and evaluation

Result visualization and model comparison

Implemented evaluation metrics:

Semantic Equivalence (GPT-4 via RAGAS)

Exact Match Accuracy

Syntax Validity (via SQLGlot)

Developed a Streamlit-based UI for real-time Text-to-SQL generation and evaluation.

🧩 System Architecture

Pipeline Steps:

Dataset Preparation — Load and format synthetic text-to-SQL data from Gretel.ai
.

Prompt Formatting — Use UnifiedDataFormatter to align inputs with model-specific instruction styles (Alpaca for LLaMA, standard for Mistral/Phi).

Fine-Tuning — Apply LoRA with the unsloth and trl libraries for efficient training.

Evaluation — Assess semantic, exact match, and syntax metrics pre- and post-tuning.

Visualization — Compare results via plots and Streamlit dashboard.

🧠 Models and Tools
Component	Purpose
Mistral-7B / LLaMA-3-8B / Phi-3-mini	Base & fine-tuned models for Text-to-SQL
LoRA (Low-Rank Adaptation)	Parameter-efficient fine-tuning
Unsloth	Fast LLM loading and fine-tuning
RAGAS + GPT-4	Semantic equivalence evaluation
SQLGlot	SQL parsing and syntax validation
Matplotlib	Performance visualization
Streamlit	UI for model comparison and live demos
📊 Results Summary
Model	Version	Semantic Equivalence	Exact Match	Syntax Validity
Mistral-7B	Base	0.45	0.20	1.00
	Fine-tuned	0.60	0.40	1.00
LLaMA-3-8B	Base	0.20	0.05	0.55
	Fine-tuned	0.45	0.35	0.95
Phi-3-mini	Base	0.45	0.10	0.85
	Fine-tuned	0.45	0.35	1.00

✅ Key Findings

Mistral-7B achieved the highest semantic and exact match gains.

LLaMA-3-8B showed the largest improvement in syntax validity.

Phi-3-mini achieved 100% syntactic correctness after tuning.

🧰 Directory Structure
NLPproject/
│
├── 111_training.ipynb        # Main training & evaluation notebook
├── demo.ipynb                # Streamlit UI for SQL generation
├── results/                  # JSON outputs of model metrics
│   ├── mistral_base_results/
│   ├── mistral_tuned_results/
│   ├── llama_base_results/
│   ├── llama_tuned_results/
│   ├── phi_base_results/
│   └── phi_tuned_results/
├── models/                   # Fine-tuned model weights & config
│   ├── mistral_tuned/
│   ├── llama_tuned/
│   └── phi_tuned/
└── README.md

⚙️ How to Run Locally (or in Colab)
1️⃣ Setup Environment
pip install unsloth datasets ragas sqlglot openai streamlit

2️⃣ Load & Fine-Tune Models

Run the cells in 111_training.ipynb to:

Load models (FastLanguageModel.from_pretrained)

Fine-tune with LoRA

Evaluate performance using RAGAS + SQLGlot

3️⃣ Run Streamlit UI (Demo)

Open demo.ipynb and execute:

Mount your drive

Start the Streamlit app (via ngrok)

Enter your OpenAI key and test prompts

Example:

https://xxxx.ngrok-free.app


You’ll see all three model outputs compared side-by-side for the same query.

🧪 Example Prompt

Input:

“List all customers living in New York.”

Generated SQL:

SELECT * FROM customers WHERE city = 'New York';

💡 Insights & Learnings

LoRA fine-tuning enables large LLMs to perform complex SQL generation without full retraining.

Semantic evaluation with GPT-4 offers a more accurate reflection of model understanding than string matching alone.

Even lightweight models (like Phi-3-mini) can achieve strong syntactic performance with targeted fine-tuning.

📚 References

Hu et al., LoRA: Low-Rank Adaptation of Large Language Models, 2021

Ram et al., RAGAS: Retrieval-Augmented Generation Assessment, 2023

Tao Mao, SQLGlot: A Python SQL Parser and Transpiler, GitHub

Gretel.ai Synthetic Text-to-SQL Dataset (Hugging Face)

Devlin et al., BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding, 2019
