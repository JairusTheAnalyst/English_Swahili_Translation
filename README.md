# English-Swahili Translation Model

A comprehensive machine translation project that fine-tunes a Helsinki-NLP transformer model for English to Swahili translation, complete with evaluation, deployment, and a web interface.

## 📋 Project Overview

This project demonstrates the complete pipeline for building a neural machine translation system:
- **Data Preprocessing**: Cleaning and preparing parallel English-Swahili text data
- **Model Fine-tuning**: Using Helsinki-NLP's opus-mt-en-sw model with TensorFlow
- **Evaluation**: BLEU score assessment using SacreBLEU metric
- **Deployment**: Interactive web interface using Gradio

## 🚀 Features

- **Pre-trained Model**: Helsinki-NLP/opus-mt-en-sw (University of Helsinki)
- **Fine-tuning**: Custom training on parallel corpus
- **Evaluation**: SacreBLEU scoring for translation quality
- **Web Interface**: Gradio-based translation app
- **Performance Comparison**: Before/after fine-tuning metrics

## 📊 Dataset

- **Size**: 8,492 parallel sentence pairs
- **Source**: Combined English-Swahili translation corpus
- **Preprocessing**:
  - Lowercasing
  - Apostrophe removal
  - Digit removal
  - Train/validation split (80/20)

## 🛠️ Installation & Requirements

```bash
# Core dependencies
pip install transformers[sentencepiece]
pip install datasets
pip install evaluate
pip install sacrebleu
pip install sacremoses

# TensorFlow for training
pip install tensorflow

# Web interface
pip install gradio

# Additional utilities
pip install pandas numpy tqdm
```

### Hardware Requirements
- **GPU**: Recommended for training (CUDA-compatible)
- **RAM**: 8GB+ for model loading
- **Storage**: 2GB+ for model checkpoints

## 🎯 Model Architecture

- **Base Model**: Helsinki-NLP/opus-mt-en-sw
- **Framework**: TensorFlow/Keras
- **Task**: Sequence-to-sequence translation
- **Max Length**: 128 tokens
- **Batch Size**: 32 (training), 16 (validation)

## 📈 Training Configuration

```python
# Training parameters
num_epochs = 2
learning_rate = 5e-5
weight_decay = 0.01
batch_size = 32
```

## 🔍 Evaluation Metrics

- **SacreBLEU Score**: Primary evaluation metric
- **Range**: 0-100 (higher is better)
- **Tokenization**: Standardized for fair comparison

## 🌐 Web Interface

The project includes a Gradio-based web interface for:
- Real-time translation
- Easy model testing
- User-friendly interaction

## 📁 Project Structure

```
English_Swahili_Translation/
├── English_Swahili_Translation.ipynb  # Main notebook
├── combined_processed                 # Preprocessed dataset (CSV)
├── final_eng-sw_translation/          # Fine-tuned model (after training)
└── README.md                         # This file
```

## 🚀 Usage

### 1. Data Preparation
```python
# Load and preprocess data
df = pd.read_csv('combined.csv')
# Apply cleaning functions
# Convert to HuggingFace dataset
```

### 2. Model Training
```python
# Load tokenizer and model
tokenizer = AutoTokenizer.from_pretrained("Helsinki-NLP/opus-mt-en-sw")
model = TFAutoModelForSeq2SeqLM.from_pretrained("Helsinki-NLP/opus-mt-en-sw", from_pt=True)

# Fine-tune
model.fit(tf_train_dataset, validation_data=tf_eval_dataset, epochs=2)
```

### 3. Translation
```python
# Load fine-tuned model
translator = pipeline("translation", model="final_eng-sw_translation")
result = translator("Hello world")
```

### 4. Web Deployment
```python
# Launch Gradio interface
interface.launch(share=True)
```

## 📊 Results

### Performance Comparison

| Model | SacreBLEU Score |
|-------|-----------------|
| Pre-trained | [Baseline Score] |
| Fine-tuned | [Improved Score] |

### Example Translations

**Input**: "i will not go to school today"

| Model | Translation |
|-------|-------------|
| Pre-trained | "Siwezi kwenda shuleni leo" |
| Fine-tuned | "Sitaenda shule leo" |
| Google Translate | "sitaenda shule leo" |

## 🔧 Key Components

### Data Preprocessing
- Text normalization
- Tokenization with SentencePiece
- Sequence padding/truncation

### Model Fine-tuning
- Transfer learning from pre-trained model
- Sequence-to-sequence architecture
- XLA compilation for performance

### Evaluation Pipeline
- Batch processing for efficiency
- SacreBLEU computation
- Progress tracking with tqdm

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📚 References

- [Helsinki-NLP Models](https://huggingface.co/Helsinki-NLP)
- [Transformers Documentation](https://huggingface.co/docs/transformers)
- [SacreBLEU Paper](https://arxiv.org/abs/1804.08771)

## 👨‍💻 Author

**JairusTheAnalyst**

## 📄 License

MIT License - see LICENSE file for details

## 🙏 Acknowledgments

- University of Helsinki for the pre-trained models
- Hugging Face for the Transformers library
- Google Colab for computational resources

---

**Note**: This project was developed as part of an NLP course curriculum, demonstrating practical application of transformer models for machine translation tasks.