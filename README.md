# Exploring SqueezeBERT

This work investigates **SqueezeBERT**, a compact and efficient NLP model designed for **mobile devices** and real-time applications. This architecture balances **accuracy** and **inference speed** by using techniques like **bottleneck layers**, **residual networks**, and **grouped convolutions**.

The project compares SqueezeBERT to **BERT-base** across multiple tasks, highlighting its performance on devices with limited computational resources.

---

## 📌 Outline

### 1. SqueezeBERT's Architecture
- **Bottleneck Layers**: Reduce input dimensionality temporarily, extract features, then expand back to focus on the most important features.  
- **Residual Networks (ResNet)**: Use skip connections to improve training stability and mitigate vanishing gradients.  
- **Grouped Convolutions**: Split channels into groups for more efficient computation while maintaining flexibility and feature specificity.  
- **BERT-based Structures**: Embedding layer → Encoder (self-attention + feed-forward layers) → Classifier.  
- **SqueezeBERT Structure**: Convolution before attention, grouped convolutions in FFN layers, 12 encoder blocks, 12 attention heads, WordPiece tokenizer.

### 2. Testing
We evaluated **SqueezeBERT** against **BERT-base** on three tasks relevant for mobile NLP:

#### Masked Language Modeling (MLM)
- **Task**: Predict masked tokens using bidirectional context.  
- **Dataset**: DailyDialog (high-quality daily conversations).  
- **Metrics**: Average Cosine Similarity between predicted and actual embeddings.  
- **Results**:

| Model        | Avg Cosine Similarity | CPU Time (sec) |
|-------------|----------------------|----------------|
| SqueezeBERT | 0.6972               | 115.056        |
| BERT-base   | 0.7820               | 174.756        |

#### Text Classification
- **Task**: Assign sentences/articles to categories.  
- **Dataset**: 3,722 English news articles across 8 categories.  
- **Metrics**: Accuracy.  
- **Results**:

| Model        | Accuracy  | CPU Time (sec) |
|-------------|-----------|----------------|
| SqueezeBERT | 0.9463    | 62.666         |
| BERT-base   | 0.9705    | 99.316         |

#### Token Classification (NER)
- **Task**: Label each token in text (Named Entity Recognition).  
- **Dataset**: CoNLL-2003 (English and German).  
- **Metrics**: Accuracy.  
- **Results**:

| Model        | Accuracy  | CPU Time (sec) |
|-------------|-----------|----------------|
| SqueezeBERT | 0.9674    | 172.922        |
| BERT-base   | 0.9756    | 300.034        |

---

## ⚡Findings
- SqueezeBERT is **1.5–1.7× faster** than BERT-base across tasks.  
- Accuracy trade-off is minimal, especially for easier tasks (NER).  
- Efficient design makes it suitable for **mobile and real-time applications**.  
- MLM task is hardest; contextual understanding affects SqueezeBERT’s performance slightly more than BERT-base.  
- Improvements in libraries over time reduce the previously reported 4× speedup.

---

## 📁 Code
The code for testing and experiments is available at:  
[https://github.com/BaioSbubens/Exploring-SqueezeBERT](https://github.com/BaioSbubens/Exploring-SqueezeBERT)

---

## 📖 References
- Iandola, F. N., et al. (2020). *SqueezeBERT: What can computer vision teach NLP about efficient neural networks?* arXiv:2006.11316.  
- Turc, I., et al. (2019). *Well-read students learn better: On the importance of pre-training compact models.* arXiv:1908.08962.  
- Sandler, M., et al. (2018). *MobileNetV2: Inverted residuals and linear bottlenecks.* CVPR.  
- He, K., et al. (2016). *Deep residual learning for image recognition.* CVPR.  
- Zhang, Z., et al. (2019). *Differentiable learning-to-group channels via groupable CNNs.* ICCV.  
- Vaswani, A., et al. (2017). *Attention is all you need.* NeurIPS.  

