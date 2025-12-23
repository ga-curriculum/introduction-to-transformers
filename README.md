# Introduction to Transformers

**Session Time:** 120 minutes

---

## Table of Contents

1. The Probabilistic Shift in NLP
2. Deep Dive: The Transformer Architecture (Attention is All You Need)
3. The Three Families: Encoders, Decoders, and Seq2Seq
4. Lab: Transformers Tour - NER, Generation, and Summarization
5. Wrap-Up and Reflection
6. Resources

---

## Learning Objectives

By the end of this module, participants will be able to:

1. **Explain** the mechanism of autoregressive text generation using probabilistic language models.
2. **Differentiate** between the three core Transformer architectures (Encoder-only, Decoder-only, Encoder-Decoder) based on their internal attention mechanisms.
3. **Evaluate** business problems to select the correct architecture family (e.g., using BERT for extraction vs. GPT for creation).
4. **Apply** specific Transformer architectures to their ideal tasks: NER (Encoder), Text Generation (Decoder), and Summarization (Seq2Seq) using established libraries.

---

## Session Breakdown

| Segment | Topic | Duration (minutes) |
| :--- | :--- | :--- |
| 1 | The Probabilistic Shift & Attention Mechanism | 30 |
| 2 | The Three Families (Encoder, Decoder, Seq2Seq) | 20 |
| 3 | Lab: Transformers Tour (Focus on Seq2Seq Summarization) | 60 |
| 4 | Wrap-Up and Reflection | 10 |

---

## 1. The Probabilistic Shift & Attention Mechanism (30 min)

* **Language Modeling as Probability:**
    * At its core, a Generative LLM is just a giant probability engine predicting $P(w_t | w_{t-1}, w_{t-2}, ...)$.
    * It doesn't "know" facts; it knows which words statistically follow other words in typical human writing.
* **The Bottleneck of RNNs (Recap):** Previous architectures (RNNs/LSTMs) had to compress an entire document into a *single* fixed-size hidden state vector before generating the next word. They "forgot" the beginning of long inputs.
* **The Breakthrough: "Attention is All You Need" (2017):**
    * **Self-Attention Mechanism:** Allows every token in a sequence to look at ("attend to") every other token simultaneously to figure out context.
    * *Example:* In the sentence "The animal didn't cross the street because **it** was too tired", attention allows the representation of "**it**" to be heavily weighted towards "**animal**" rather than "street".

## 2. The Three Families (20 min)

Not all Transformers are created equal. Depending on how we wire the attention blocks, we get three distinct families suited for different tasks.

| Architecture | Core Mechanism | Best For... | Famous Examples |
| :--- | :--- | :--- | :--- |
| **Encoder-Only** | Bi-directional attention (looks at whole sentence at once). | Understanding, Classification, NER, Extractive QA. | BERT, RoBERTa, DistilBERT |
| **Decoder-Only** | Uni-directional / Causal attention (can only look at past words). | Text Generation, Chatbots, Code Completion. | GPT-3/4, Llama, Bloom |
| **Encoder-Decoder (Seq2Seq)** | Encoder understands input, Decoder generates output. | Translation, Summarization, Paraphrasing. | T5, BART, MarianMT |

* **Key Decision Framework:**
    * *Do you need to assign a label to existing text?* -> **Encoder**.
    * *Do you need to create completely new text from a prompt?* -> **Decoder**.
    * *Do you need to transform one text into another (keeping roughly similar semantic content)?* -> **Seq2Seq**.

## 3. Lab: Transformers Tour (60 min)

**Objective:** Go beyond the high-level `pipeline` and interact with specific model architectures for their designated tasks, with a deep dive into summarization.

### Refer: [Summarizer in Action](https://git.generalassemb.ly/applied-ai-and-deep-learning-in-action/Lab-3_3-Summarizer-in-Action)

## 4. Wrap-Up and Reflection (10 min)

**Reflection Questions:**

1.  Why can't a Decoder-only model (like GPT) easily perform standard classification tasks as efficiently as BERT? (Hint: Think about how it reads text—left-to-right only vs. all-at-once).
2.  When summarizing sensitive financial documents, would you prefer a higher or lower "temperature" setting in your generation parameters? Why?
3.  T5 treats every problem as a text-to-text problem (even classification!). How does this differ from the specialized "heads" we used in BERT?

---

## 5. Resources

* [The Illustrated Transformer (Jay Alammar)](https://jalammar.github.io/illustrated-transformer/) - *The definitive visual guide to the architecture.*
* [Attention Is All You Need (Original Paper)](https://arxiv.org/abs/1706.03762)
* [Hugging Face Tasks Guide](https://huggingface.co/tasks) - *Excellent reference for matching architectures to business problems.*