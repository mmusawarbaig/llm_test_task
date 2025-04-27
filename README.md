# Thermodynamic State Identification using LLMs

## Overview

This exploration is about evaluating the ability of latest state of the art Large Language Models (LLMs) to classify thermodynamic changes of state (e.g., adiabatic, isothermal, isobaric) from given thermodynamic problem descriptions.

## Files

* `main.ipynb`: Jupyter Notebook with code, experiments, and results.
* `GitHub_Link.txt`: Repository link.
* `README.md`: Brief documentation of the test task.

## Approach

* Loading the given dataset.
* Exploring the given dataset
* Cleaning the given dataset to remove unnessary details
* Create multiple diverse prompt templates.
* Querying modern LLMs (like qwen2.5:3b, llama3.1:8b, gemma3:12b, and llama-3.3-70b etc).
* Comparing model outputs to true labels.
* Analyzing accuracy
* Observing the effect of different prompting styles and model size on the Accuracy.

## How to Run the Code

1. Clone the repository.
2. Install required packages:
   ```bash
   pip install pandas ollama groq python-dotenv matplotlib
   ```
3. Open and run `main.ipynb` in Jupyter.
4. Additional steps needed for exprementation with LLMs (like llama-3.3-70b-versatile) hosted by [Groq](https://groq.com/).
   a. Make a ".env" file and add your Groq API key like "GROQ_API_KEY="PASTE_YOUR_API_KEY_HERE" in the file.
   b. Uncomment the GROQ API code in "Classifications using LLM" section and comment out the Ollama API code.
   c. Run `main.ipynb`

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
| **llama-3.3-70b-versatile** (from **Groq**) | %                |

> 🧠 **Note:** Accuracy improves significantly with larger and more capable models.

### Observations and Potential Improvements

Despite testing with various LLMs — including **qwen2.5:3b**, **llama3.2:latest (3b)**, **phi3:3.8b**, **llama3.1:8b**, **gemma3:12b**, and **llama-3.3-70b** — the final results (as recorded in the above table) showed **low classification accuracy** across all models.

#### Key Insights:

- Even state-of-the-art LLMs struggled with the specialized domain of thermodynamic problem classification.
- This suggests that **general-purpose LLMs** may require domain-specific adaptation for better performance.

#### Future Directions for Improvement:

- **Fine-tuning** the models on a curated dataset of thermodynamic problems to specialize them for this task.
- **Enhancing prompt engineering** to better align with the complexity and structure of thermodynamic questions.
- **Exploring additional LLMs** to identify models that may inherently align better with the problem characteristics.

> 🚀 **Summary:** Tailoring the models and prompts to the domain can significantly boost accuracy for specialized tasks like thermodynamics.
>

**Task Completed by:** [Muhammad Musawar Baig](https://www.linkedin.com/in/muhammad-musawar-baig-mmb/)

**Last Updated:** April 27th, 2025

---
