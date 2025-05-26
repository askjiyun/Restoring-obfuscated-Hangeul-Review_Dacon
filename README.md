# Restoring-obfuscated-Hangeul-Review_Dacon
난독화된 한글 리뷰 복원 AI 경진대회 

## Model Checkpoints
This repository contains multiple fine-tuned model checkpoints developed for the Dacon competition on restoring obfuscated Korean reviews.

---
## Download Models
All model checkpoints are bundled as a single `.zip` file and available via Google Drive. 

📥 **Download Link**  
[🔗 Click here to download the full model archive](https://drive.google.com/file/d/1Otffk1vPcetD758IK2TWV68mT2qYUsMP/view?usp=drive_link)

Or download via command line:
```bash
pip install gdown
gdown "https://drive.google.com/file/d/1Otffk1vPcetD758IK2TWV68mT2qYUsMP/view?usp=drive_link" --output model.zip
unzip model.zip
```
---
### Included Checkpoints
The archivvve contains the following folders under `model`/:
- `best_model_0116_v2/`
- `best_model_augmented/`
- `output_0214/`
- `output_0224/`
- `pko_augmented/`
- `pko_best_model/`
- `pko-t5-review-restoration/`

Each folder includes:

- Model config (`config.json`)
- Tokenizer files
- Model weights (`pytorch_model.bin` or `model.safetensors`)
- Optimizer files (may be split as `optimizer.pt.part_*`)

---
### How to use

Choose a folder (e.g. `model/pko_augmented`) and load the model with Hugging Face Transformers:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

model_path = "model/pko_augmented"
tokenizer = AutoTokenizer.from_pretrained(model_path)
model = AutoModelForSequenceClassification.from_pretrained(model_path)
```

If `optimizer.pt` is split into multiple parts, restore it like this:
```bash
cd model/pko_augmented
cat optimizer.pt.part_* > optimizer.pt
```
