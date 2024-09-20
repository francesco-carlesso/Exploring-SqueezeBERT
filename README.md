# Exploring SqueezeBERT
Mobile devices (especially smartphones) stand out as crucial platforms for implementing NLP models. However, smaller devices cannot afford the enormous computational costs associated with existing high-accuracy NLP models, such as BERT and RoBERTa. We propose an analysis of the SqueezeBERT model, starting from the results presented in some papers that address computer vision techniques applied to NLP tasks. 

## Project Outline
1. ***SqueezeBERT's Architecture:*** Giving a theoretical overview of the model's main architectural components, such as: Bottleneck Layers, Residual Networks, and Grouped Convolutions. 
2. ***Testing:*** Performing tests with the model on three relevant tasks for mobile devices, and comparing it to the BERT original model using some performance metrics and CPU time.
   - *Masked Language Modeling:* Predicting a masked token in a sequence
   - *Text Classification:* Assigning a sentence or document to an appropriate category
   - *Token Classification:* Identifying specific entities within a text (NER)

The code for the testing part is available at [this repository](https://github.com/BaioSbubens/Exploring-SqueezeBERT).
