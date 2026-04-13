# Encoder-Decoder and Attention Mechanism for Neural Machine Translation

---

# Objective

* Understand sequence-to-sequence (Seq2Seq) models
* Build encoder-decoder architecture using GRU
* Implement machine translation (English → Spanish)
* Learn greedy decoding and beam search
* Understand and implement attention mechanism

---

# Dataset

* English–Spanish translation dataset

* Contains:

  * Source text (English)
  * Target text (Spanish)

* Split into:

  * Training set
  * Validation set
  * Test set

---

# Tokenization

* Used BPE tokenizer
* Vocabulary size limited to 10,000

Special tokens:

* `<pad>` – padding
* `<unk>` – unknown tokens
* `<s>` – start of sentence
* `</s>` – end of sentence

Learning:

* Start and end tokens are required for sequence generation

---

# Data Preparation

* Tokenized both source and target text

* Created:

  * Token IDs
  * Attention masks

* Target shifted for training:

  * Input → `<s> sentence`
  * Label → `sentence </s>`

---

# Custom Batch Handling

* Implemented collate function
* Combined:

  * Source tokens + mask
  * Target tokens + mask

Learning:

* Required for handling variable-length sequences

---

# Encoder-Decoder Architecture

Model components:

* Embedding layer
* Encoder (GRU)
* Decoder (GRU)
* Linear output layer

Flow:

1. Source sequence → Encoder
2. Encoder produces hidden state
3. Hidden state passed to Decoder
4. Decoder generates output sequence

---

# Packed Sequences

* Used pack_padded_sequence
* Avoids unnecessary computation on padded tokens

Learning:

* Improves efficiency and training quality

---

# Loss Function

* CrossEntropyLoss
* Ignored `<pad>` tokens

---

# Training Strategy

* Optimizer: NAdam
* Metric: Accuracy
* Learning rate scheduling applied
* Validation after each epoch

---

# Greedy Decoding

* Select highest probability token at each step

Issue:

* Can produce incorrect translations
* Errors accumulate

---

# Beam Search

* Keeps top-k candidate sequences
* Explores multiple possibilities

Features:

* Beam width controls number of candidates
* Length penalty balances short vs long outputs

Learning:

* Produces better translations than greedy decoding

---

# Attention Mechanism

Implemented:

* Query = Decoder outputs
* Key = Encoder outputs
* Value = Encoder outputs

Process:

* Compute similarity scores
* Apply softmax to get attention weights
* Combine weighted encoder outputs

Learning:

* Allows model to focus on relevant words
* Solves information bottleneck problem

---

# Encoder-Decoder with Attention

Changes:

* Used encoder outputs instead of only final hidden state
* Combined attention output with decoder output

Result:

* Improved translation quality
* Better handling of long sentences

---

# Key Learnings

* Seq2Seq models map one sequence to another
* Encoder compresses input into hidden representation
* Decoder generates output step-by-step
* Greedy decoding is simple but limited
* Beam search improves sequence generation
* Attention allows dynamic focus on input tokens
* Handling padding correctly is essential

---

# Conclusion

This project builds a strong understanding of neural machine translation using encoder-decoder architecture. By extending the model with attention and improving decoding strategies, it demonstrates how sequence models can generate more accurate and context-aware translations.

---
