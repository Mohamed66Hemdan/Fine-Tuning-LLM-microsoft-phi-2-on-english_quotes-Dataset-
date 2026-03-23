# Fine-Tuning Phi-2 with LoRA for Keyword Extraction

## Overview
- This project focuses on fine-tuning a Large Language Model (LLM) to perform a specialized Natural Language Processing (NLP) task: extracting descriptive keywords from text.
- The model is trained to identify words that describe a person's **skills, personality, or emotional state** from a given sentence.
- Instead of full model training, the project uses **LoRA (Low-Rank Adaptation)**, a parameter-efficient fine-tuning technique that significantly reduces computational cost while maintaining strong performance.

---
## Objective
The main goal is to transform a general-purpose language model into a task-specific model capable of:

- Understanding sentence context
- Identifying descriptive attributes
- Producing clean, structured keyword outputs

---

## Approach

### 1. Base Model
- The project uses a pre-trained transformer-based language model as the foundation.

### 2. Parameter-Efficient Fine-Tuning (LoRA)
Instead of updating all model weights, only a small subset of parameters is trained. This approach:
- Reduces memory usage
- Speeds up training
- Makes the process feasible on limited hardware (e.g., Google Colab)
---
### 3. Dataset Preparation
The project uses the **English Quotes Dataset**, which contains a collection of inspirational and philosophical quotes collected from Goodreads.

This dataset consists of approximately 2,500 text samples, where each sample includes:
- A quote (main text)
- The author of the quote
- A set of tags describing the themes or topics of the quote :contentReference[oaicite:0]{index=0}
  
#### Data Preprocessing
- The dataset is converted into an instruction-style format to guide the model toward the keyword extraction task  
- Each input clearly defines the task and provides the sentence as context  
- Text is tokenized into numerical representations suitable for the model  
- Padding and truncation are applied to ensure consistent input sizes  
- A padding token is explicitly defined for stable batch processing  

These tags act as semantic labels such as *love, life, motivation, success, philosophy*, and more. :contentReference[oaicite:1]{index=1}

### 4. Training Strategy

The model is trained using a combination of efficient training techniques, structured preprocessing, and carefully selected hyperparameters.

#### Training Approach
- A causal language modeling objective is used, where the model learns by predicting the next token  
- This enables the model to implicitly learn how to generate structured keyword outputs  
- The model is trained for multiple epochs to reinforce task understanding  

#### Hyperparameters
- A small batch size is used due to hardware limitations  
- Gradient accumulation simulates a larger effective batch size and improves stability  
- A low learning rate ensures gradual adaptation without harming pre-trained knowledge  
- Warmup steps are applied to stabilize training in early stages  
- Mixed precision (FP16) reduces memory usage and speeds up training  

#### Optimization & Monitoring
- Training progress is logged at regular intervals  
- Model checkpoints are saved periodically  
- A limit is set on saved checkpoints to manage storage efficiently  
- Caching is disabled during training to ensure correct gradient updates  
---

## Results


---

## Model Saving & Reuse
The fine-tuned model is saved in a lightweight format, allowing:
- Easy reuse
- Fast loading
- Deployment in other applications

---

## Use Cases

This approach can be extended to:

- Sentiment analysis
- Personality detection
- Resume analysis (skills extraction)
- Social media text analysis
- Chatbot response refinement

---

## Key Learnings

- Parameter-efficient methods like LoRA are highly effective for LLM fine-tuning
- Prompt design plays a critical role in model performance
- High-quality data is more important than large quantities
- Fine-tuning significantly improves task-specific behavior

---

## Future Improvements

- Use a more domain-specific dataset
- Enhance prompt engineering techniques
- Apply instruction tuning for better generalization
- Evaluate performance using quantitative metrics
- Experiment with larger or more advanced models

---

## 👨‍💻 Author

Mohamed Hamdan  
AI Engineer
