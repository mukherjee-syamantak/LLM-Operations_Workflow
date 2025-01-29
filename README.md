# LLM Operations Workflow Implementation

This project is part of the deeplearning.ai LLMOps course and demonstrates a comprehensive workflow for working with large language models (LLMs). The implementation spans three interconnected Jupyter notebooks, each focusing on a different phase of the process: data preparation, pipeline automation, and prediction with safety checks. Below is a detailed overview of the project structure, purpose, and tools utilized.

---

## Project Structure

### Notebook 1: `L2_data_updated.ipynb`
#### **Purpose**: Data Preparation
This notebook focuses on preparing and processing data for fine-tuning a language model. It ensures the availability of clean and relevant data for subsequent training.

**Key Steps:**
1. **Authentication and Setup**:
   - Connects to Google Cloud and initializes the environment for interacting with BigQuery.

2. **Data Retrieval**:
   - Queries Stack Overflow datasets from BigQuery to fetch Python-related questions and accepted answers.
   - Filters questions based on tags and time constraints.

3. **Data Processing**:
   - Combines question titles and bodies as input text and uses accepted answers as output text.
   - Formats the data in an instruction-based structure suitable for fine-tuning.

4. **Train-Test Split**:
   - Splits data into training and evaluation sets.

5. **Exporting Data**:
   - Saves the processed data in `.jsonl` format for use in subsequent steps.

**Outcome**: Cleaned and formatted datasets ready for fine-tuning and evaluation.

---

### Notebook 2: `L3_automation.ipynb`
#### **Purpose**: Pipeline Automation
This notebook automates the process of fine-tuning large language models using Kubeflow Pipelines (KFP), enabling reproducibility and scalability.

**Key Steps:**
1. **Pipeline Components**:
   - Defines modular and reusable components for tasks like data processing, model training, and evaluation.

2. **Pipeline Definition**:
   - Creates an end-to-end pipeline using `kfp.dsl.pipeline`.
   - Connects components to automate workflows, from data ingestion to evaluation.

3. **Pipeline Compilation**:
   - Converts the pipeline into a YAML specification deployable on a Kubernetes cluster.

4. **Parameterization**:
   - Allows customization of parameters such as model name, training steps, and dataset locations for flexibility.

**Outcome**: A deployable pipeline for automating fine-tuning workflows and ensuring efficient execution.

---

### Notebook 3: `L4_predictions_prompts_safety.ipynb`
#### **Purpose**: Predictions and Safety Evaluation
This notebook demonstrates how to use fine-tuned models for generating predictions while emphasizing response safety and quality.

**Key Steps:**
1. **Model Deployment**:
   - Retrieves tuned models from Vertex AI and initializes them for prediction tasks.

2. **Prompt Engineering**:
   - Crafts structured prompts to guide the model in generating context-aware and accurate responses.
   - Example prompts include answering Stack Overflow-style questions.

3. **Safety Checks**:
   - Evaluates model outputs for safety attributes, such as blocked content or unsafe responses.
   - Extracts safety attributes and citations from responses for analysis.

4. **Testing and Benchmarking**:
   - Tests the model with various prompts (e.g., explaining Python concepts or completing sentences).
   - Ensures factual accuracy by verifying citations.

**Outcome**: A framework for generating high-quality, safe predictions using fine-tuned LLMs.

---

## Tools and Frameworks Used
- **Google Cloud Platform**:
  - BigQuery for data retrieval.
  - Vertex AI for model fine-tuning and deployment.
  - PaLM 2 and text-bison@001 models for responses tailored to specific prompts, ensuring robust and accurate outputs
- **Kubeflow Pipelines (KFP)**:
  - For automating workflows with reusable components.
- **Python Libraries**:
  - Data Science: `pandas`, `numpy`.
  - ML Workflow: `kfp`, `scikit-learn`.
- **Other Tools**:
  - `Arrow from Apache Framework` for data processing.

---

## Key Concepts Illustrated
- **Data Engineering**:
  - Querying, cleaning, and preparing datasets for ML model training.
- **ML Pipelines**:
  - Automating workflows using modular and reusable components.
- **Prompt Engineering**:
  - Structuring inputs to achieve desired behavior from LLMs.
- **Safety and Reliability**:
  - Ensuring outputs are safe, accurate, and free from harmful content.

---

## How to Use
1. Clone the repository and install required dependencies.
   ```bash
   git clone <repository_url>
   cd <repository_name>
   pip install -r requirements.txt
   ```

2. Authenticate with Google Cloud and set up your project ID.

3. Execute the notebooks in sequence:
   - `L2_data_updated.ipynb` for data preparation.
   - `L3_automation.ipynb` to run fine-tuning pipelines.
   - `L4_predictions_prompts_safety.ipynb` for testing and evaluation.

4. Customize pipeline parameters as needed in `L3_automation.ipynb`.

---

## Results
This workflow enables efficient fine-tuning of LLMs with high-quality data, ensuring safe and context-aware predictions. It serves as a robust example of LLMOps practices for real-world applications.
