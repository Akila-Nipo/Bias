# Political-Gender-Bias-Bengali-LLMs

This repository provides a reproducible framework for evaluating political and gender bias in Bengali large language models. The project combines two probing strategies:

- Natural probing, using masked sentence prompts derived from natural language contexts
- Template probing, using structured prompts that target political and gender-related attributes

## Project overview

The workflow is organized around three main stages:

1. Benchmark data generation
2. Model inference and prediction collection
3. Metric computation, statistical testing, and visualization

The codebase is structured to support experiments across multiple LLM backends, including Hugging Face, OpenAI-compatible APIs, and Gemini.

## Repository structure

- benchmark/
  - natural_probing/: scripts for creating masked-sentence probes
  - template_probing/: scripts for generating template-based prompts
- data/
  - natural_probing/: masked sentence datasets
  - template_probing/: prompt templates, adjective lists, occupations, and generated prompts
- evaluation/
  - natural_probing/: inference, metrics, significance tests, and visualization
  - template_probing/: inference, metrics, significance tests, and visualization
- models/
  - model interfaces and registry for different model providers
- model_outputs/
  - generated predictions for each evaluated model
- results/
  - analysis figures, metrics, statistics, and tables

## Setup

Requirements:

- Python 3.10+
- A virtual environment is recommended

Install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate   # Windows PowerShell
pip install -r requirements.txt
```

## Running the pipeline

### 1. Generate prompts

For template-based probing:

```bash
python benchmark/template_probing/generate_prompts.py
```

This creates the generated prompt set under the data/template_probing directory.

### 2. Run model inference

Inference entry points are organized under the evaluation modules:

```bash
python evaluation/natural_probing/run_inference.py
python evaluation/template_probing/run_inference.py
```

### 3. Compute metrics and analyze results

```bash
python evaluation/natural_probing/compute_metrics.py
python evaluation/template_probing/compute_metrics.py
python evaluation/natural_probing/significance_tests.py
python evaluation/template_probing/significance_tests.py
python evaluation/natural_probing/visualize.py
python evaluation/template_probing/visualize.py
```

## Outputs

The repository saves:

- model predictions in model_outputs/
- computed evaluation metrics in results/metrics/
- statistical test outputs in results/statistics/
- plots and figures in results/figures/
- summary tables in results/tables/

## Notes

- Model backends and credentials are handled through the modules in the models/ directory.
- The project is designed to be extended with additional models, datasets, and evaluation metrics as needed.
- For reproducibility, keep the generated prompt files and model output files together with the corresponding experiment configuration.

## License

This project is distributed under the terms of the repository license.

