# Copilot Instructions for LearnRAG

## Project shape and intent
- This repo is notebook-first and lives under LocalLLM/. There are no Python packages or scripts yet.
- Core flow: download a small Hugging Face model (distilgpt2) -> save it under LocalLLM/downloaded_model/ -> reload and run text-generation.
- The notebooks are exploratory and demonstrate model internals (config, weights, tokenizer) plus basic generation.

## Key notebooks and what they show
- LocalLLM/DeconstructLLM.ipynb: downloads distilgpt2, saves artifacts, then inspects config.json, tokenizer config, vocab, and weight tensors.
- LocalLLM/RunandGenerate.ipynb: installs dependencies, downloads distilgpt2, saves it, and runs text generation with transformers.pipeline.
- LocalLLM/LLMPipeline.ipynb: outlines the end-to-end LLM pipeline (tokenization -> ids -> model -> next token).

## Data and artifacts
- LocalLLM/downloaded_model/ is the expected local cache for model + tokenizer artifacts.
- Notebooks assume save_directory = "./downloaded_model" when run from LocalLLM/.

## Environment and workflow
- Dependencies used in notebooks: transformers, torch, torchvision, safetensors.
- Typical install cells include `!uv pip install transformers` and `pip install torch torchvision`.
- There are no tests or CLI entry points; execution happens cell-by-cell in notebooks.

## Conventions to follow
- Keep changes notebook-centric unless the user asks for scripts or packaging.
- When adding code, align with the existing pattern of using AutoModelForCausalLM and AutoTokenizer, plus pipeline for generation.
- If you add new artifacts, keep them under LocalLLM/ or LocalLLM/downloaded_model/ and update the related notebook text.
