# Strive-Ewe Hybrid Tokenizer (v1.0)

## Performance & Metrics
- **Fertility Score (Ewe):** 1.157 tokens/mot (Gain de +47.45%)
- **Efficiency:** Processus environ 90% de texte en plus dans la même fenêtre de contexte.
- **New Tokens:** 180,363 nouveaux tokens spécifiques à l'Ewe.

## Overview
This is a hybrid tokenizer for the **Ewe (ɛʋɛgbɛ)** language, designed by **Strive** to address the limitations of global multilingual models. 
By expanding the **XLM-RoBERTa** base vocabulary with over 180,000 language-specific tokens, we significantly reduce subword fragmentation.

## Performance & Metrics

### 1. Fragmentation Efficiency (Fertility Score)
The fertility score measures the average number of tokens produced per word. A lower score indicates better morphological alignment.

| Model | Fertility Score (Ewe) | Efficiency Gain |
| :--- | :---: | :---: |
| XLM-RoBERTa Base | 2.202 | - |
| **Strive-Ewe Hybrid** | **1.157** | **+47.45%** |

### 2. Context Window Optimization
By reducing the number of tokens per sentence, this tokenizer allows the model to process approximately **90% more Ewe text** within the same context window (512 tokens) compared to the standard XLM-R tokenizer.

### 3. Vocabulary Insights
- **New Tokens Added:** 180,363
- **Base Model:** XLM-RoBERTa-Base
- **Training Data:** 1M+ sentences (NLLB-200 + Bible + Strive Custom Instruct Dataset)

## Visual Comparison (Example)
**Sentence:** *"Akpe ene kple alafa atɔ̃ nye alafa eve blata-atɔ̃."*

- **XLM-R Base (23 tokens):** `['_Ak', 'pe', '_en', 'e', ...]`
- **Strive-Ewe (12 tokens):** `['_Akpe', '_ene', '_kple', '_alafa', ...]`

## Training Methodology
The tokenizer was trained using the `Unigram` algorithm via the `train_new_from_iterator` method. 
It preserves the original 250k XLM-R tokens to maintain multilingual compatibility with French and other languages while optimizing for the specific phonology and morphology of Ewe (notably handling special characters like **ɖ, ɛ, ƒ, ɣ, ɦ, ŋ, ɔ, ʋ**).

## How to Use
```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("jojonocode/strive-ewe-xlmr-hybrid-tokenizer")

text = "Eʋegbe nye gbe nyui de."
tokens = tokenizer.tokenize(text)
print(tokens)

If you use this tokenizer in your research, please cite:

@software{strive_ewe_tokenizer_2026,
  author = {Joël ADZONYA Elisée, Strive Team},
  title = {Strive-Ewe Hybrid Tokenizer: Optimizing XLM-RoBERTa for Ewe Language},
  year = {2026},
  url = {[https://huggingface.co/](https://huggingface.co/){repo_id}}
}
