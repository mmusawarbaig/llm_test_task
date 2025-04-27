# Thermodynamic State Identification using LLMs

## Overview

This task focuses on evaluating the capability of the latest state-of-the-art Large Language Models (LLMs) to classify thermodynamic changes of state—such as adiabatic, isothermal, isochoric, isobaric, polytropic, isenthalpic, and isentropic—directly from natural-language thermodynamic problem descriptions.

The workflow involved exploring and cleaning the provided dataset, designing multiple prompt templates, and querying various modern LLMs, including qwen2.5:3b, llama3.1:8b, gemma3:12b, and llama-3.3-70b (via Groq API). The model outputs were compared against ground-truth labels to evaluate classification accuracy and study how different prompt writing styles and model sizes effect the performance.

Experiments revealed that role-based instruction prompts consistently achieved the highest accuracy among the prompting techniques tested. The observations highlighted that larger models like gemma3:12b and llama-3.3-70b performed slightly better (~17% accuracy), although even advanced LLMs struggled with reliably classifying thermodynamic states without domain-specific fine-tuning.

The results highlight that general-purpose LLMs require domain adaptation to effectively handle specialized scientific tasks like thermodynamic state identification. The results also suggests that prompt engineering and semantic understanding are critical factors impacting LLM performance in technical domains.

## Files

* `main.ipynb`: Jupyter Notebook with code, experiments, and results.
* `GitHub_Link.txt`: Github repository link.
* `README.md`: Brief documentation of the test task.

## Approach

* Loading the given dataset.
* Exploring the given dataset
* Cleaning the given dataset to remove unnessary details
* Create multiple diverse prompt templates.
* Querying modern LLMs (like qwen2.5:3b, llama3.1:8b, gemma3:12b, and llama-3.3-70b etc).
* Comparing model outputs to true labels and accuracy calculations.
* Analyzing accuracy
* Observing the effect of different prompting styles and model size on the Accuracy.

## How to Run the Code

1. Clone the repository: git
2. ```bash
   git clone https://github.com/mmusawarbaig/llm_test_task.git
   ```
3. Install required packages:

   ```bash
   pip install pandas ollama groq python-dotenv matplotlib
   ```
4. Download the given dataset using the link provided in the task discription file titled "Charu_KnowTD assisted LLM Retrieval of Relevant Equations for Thermodynamics Problems.pdf"
5. Downlaod and install Ollama for running the LLMs locally depening on your opearating system as per the instructions [here](https://github.com/ollama/ollama).
6. Download and install the model the you want to experiment (e.g by running "ollama pull gemma3:12b" using Ollama CLI)
7. Set the model name in the "Classifications using LLM" section of code like "ollama_model_name = "gemma3:12b" for gemma3:12b or any other model of your choice that you want to experiment with.
8. Open and run `main.ipynb`.
9. Additional steps needed for exprementation with LLMs (like llama-3.3-70b-versatile) hosted by [Groq](https://groq.com/). You can skip these steps if you only want to only run LLMs locally using [Ollama](https://ollama.com/):
   a. Make a ".env" file and add your Groq API key like GROQ_API_KEY="PASTE_YOUR_API_KEY_HERE" in that file.
   b. Set "USE_GROQ_API = True" in the "Classifications using LLM" section of code and make USE_OLLAMA_API = False.

   c. Set model name of the model hosted by Groq like groq_model_name = "llama-3.3-70b-versatile" if you want to experiment with llama-3.3-70b-versatile.

   d. Run `main.ipynb`

## Results

### Prompt Style Analysis

I observed the highest accuracy using a **Role-Based Style Instruction Prompt**.

For diverse prompt formulations using the **"llama3.1:8b"** model, with results across four different prompt styles:

- **Direct Instruction Prompt Template**: 14.77% Accuracy
- **Checklist-Style Command Prompt Template**: 13.55% Accuracy
- **Example-Based (Few-Shot) Prompt Template**: 11.84% Accuracy
- **Role-Based Instruction Prompt Template**: **16.12% Accuracy**

For diverse prompt formulations using the **"gemma3:12b"** model, with results across four different prompt styles:

- **Direct Instruction Prompt Template**: 16.97% Accuracy
- **Checklist-Style Command Prompt Template**: 14.41% Accuracy
- **Example-Based (Few-Shot) Prompt Template**: 15.26% Accuracy
- **Role-Based Instruction Prompt Template**: **17.34% Accuracy**

> 📈 **Insight:** The role-based instruction prompt has achieved the highest performance among the styles tested.

### Model-Wise Overall Accuracy Comparison

The overall accuracy (calculated as the average of per-problem accuracies) for different models (using Role-Based Style Instruction Prompt Template) is as follows:

| Model                                                   | Overall Accuracy |
| ------------------------------------------------------- | ---------------- |
| **qwen2.5:3b**                                    | 12.21%           |
| **phi3:3.8b**                                     | 4.64%            |
| **llama3.2:latest (3b)**                          | 14.41%           |
| **llama3.1:8b**                                   | 16.12%           |
| **gemma3:12b**                                    | 17.34%           |
| **llama-3.3-70b-versatile** (from **Groq**) | 17.34%           |

> 🧠 **Note:** Accuracy improves significantly with larger and more capable models.

### Observations and Potential Improvements

Despite testing with various LLMs — including **qwen2.5:3b**, **llama3.2:latest (3b)**, **phi3:3.8b**, **llama3.1:8b**, **gemma3:12b**, and **llama-3.3-70b** — the final results (as recorded in the above table) showed **low classification accuracy** across all models.

#### Key Insights:

- Even state-of-the-art LLMs struggled with the specialized domain of thermodynamic problem classification.
- This suggests that **general-purpose LLMs** may require domain-specific adaptation for better performance.

* **Bigger models don't always guarantee better accuracy:** Even though **gemma3:12b** and **llama-3.3-70b-versatile** are large models, their accuracy was similar (~17.34%). This suggests that just increasing model size does not automatically improve performance for specialized tasks like thermodynamics.
* **Task-specific knowledge matters more than model size:** Without being fine-tuned on thermodynamics data, even large models perform similarly to smaller ones, showing the importance of **domain adaptation** over raw model scale.

#### Future Directions for Improvement:

- **Fine-tuning** the models on a curated dataset of thermodynamic problems to specialize them for this task.
- **Enhancing prompt engineering** to better align with the complexity and structure of thermodynamic questions.
- **Exploring additional LLMs** to identify models that may inherently align better with the problem characteristics.

> 🚀 **Summary:** Tailoring the models and prompts to the domain can significantly boost accuracy for specialized tasks like thermodynamics.

**Task Completed by:** [Muhammad Musawar Baig](https://www.linkedin.com/in/muhammad-musawar-baig-mmb/)

**Last Updated:** April 27th, 2025

---
