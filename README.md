# Infix to Postfix Seq2Seq Models

This repository contains implementations of neural network models that convert mathematical expressions from **infix** to **postfix** notation using sequence-to-sequence learning. It includes:

- A baseline LSTM Seq2Seq model  
- An LSTM Seq2Seq model with **Luong-style attention**  
- A full **Transformer** encoder-decoder model  

All models are implemented in **Keras (TensorFlow backend)** and designed to run on **Google Colab**.

---

## Project Structure

```
infix-to-postfix-seq2seq-models/
│
├── LSTM-EncoderDecoder.ipynb                   # Basic Encoder-Decoder with LSTM
│
├── Luong-Attention-Seq2Seq.ipynb               # LSTM with Luong-style Attention
│
├── Transformer-Based-Seq2Seq.ipynb             # Transformer Encoder-Decoder version
│
└── README.md
```

---

## Final Model Comparison

| Model Type         | Prefix Accuracy (avg ± std) | Trainable Params |
|--------------------|-----------------------------|------------------|
| Baseline Seq2Seq   | 0.979 ± 0.019               | ~200k            |
| Luong Attention    | 1.000 ± 0.000               | ~800k            |
| Transformer        | 1.000 ± 0.000               | ~1.5M            |

>  **Note**: Despite slightly lower accuracy, the baseline model was selected for final deployment due to its simplicity and lower computational cost.

---

##  Dataset Generation

Synthetic data is generated on-the-fly using a rule-based infix-to-postfix generator. It supports:

- Digits (0–9)  
- Operators: `+`, `-`, `*`, `/`  
- Parentheses

---

## Training and Inference

- **Loss**: `sparse_categorical_crossentropy`  
- **Metric**: `masked_accuracy` to ignore padding tokens  
- **Inference**: Autoregressive decoding is used for final predictions  

---

## Model Weights

Trained weights are publicly accessible via [Google Drive](https://drive.google.com/file/d/1ZI89h7LchbNfQ3w_FXzZd-WBX4P57qfn/view?usp=share_link) and can be downloaded with `gdown`:

```bash
pip install gdown
gdown https://drive.google.com/uc?id=1ZI89h7LchbNfQ3w_FXzZd-WBX4P57qfn
```

---

## How to Run

- Open `.ipynb` files in Google Colab  
- Make sure dependencies like `TensorFlow` and `NumPy` are installed  
- Run all cells from top to bottom  
- To evaluate the model, run the `test()` function at the end

---
