# Thermodynamic State Identification using LLMs

## Overview

This exploration is about evaluating the ability of latest state of the art Large Language Models (LLMs) to classify thermodynamic changes of state (e.g., adiabatic, isothermal, isobaric) from given thermodynamic problem descriptions.

## Files

* `main.ipynb`: Jupyter Notebook with code, experiments, and results.
* `GitHub_Link.txt`: Repository link.
* `README.md`: Brief documentation of the task.

## Approach

* Loading the given dataset.
* Exploring the given dataset
* Cleaning the given dataset to remove unnessary details
* Create multiple prompt templates.
* Querying modern LLMs (including qwen2.5:3b, llama3.1:8b, and llama-3.3-70b).
* Comparing model outputs to true labels.
* Analyzing accuracy and misclassifications.

## How to Run the Code

1. Clone the repository.
2. Install required packages:
   ```bash
   pip install pandas ollama groq python-dotenv
   ```
3. Open and run `main.ipynb` in Jupyter.
4. Additional steps needed for exprementation with LLMs hosted by groq:
   a. Make a ".env" file and add your Groq API key like "GROQ_API_KEY="PASTE_YOUR_API_KEY_HERE" in the file.
   b. Uncomment the GROQ API code in "Classifications using LLM" section and comment out the Ollama API code.
   c. Run `main.ipynb`

## Results

* Observed low classification accuracy (final results in notebook) on varions tested LLMs including qwen2.5:3b, llama3.1:8b, and llama-3.3-70b. We can improve the accuracy by fine-tuning LLMs on dataset of thermodynamic problems, further improving the prompts and exploring more LLMs (to see which one fits best in the provided use case)).
* Detailed analysis of prompt engineering and model performance included.

---

Last Updated: April 26th, 2025

---
