



# <div align="center">TextLessRAG: End-to-end Visual Document RAG by Speech without Text<div>

<div align="center">
<!-- <h1>A Multi-round Multi-modal Reinforcement Learning Framework</h1> -->
<p><strong>An end2end OCR & ASR & TTS free multimodal retrieval-augmented generation pipeline </strong></p>

<a href='https://huggingface.co/datasets/hit12345/textlessrag/tree/main'><img src='https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Datasets-green'></a>
<a href="https://huggingface.co/vidore/colqwen-omni-v0.1" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Retriver-blue></a>
<a href="https://huggingface.co/Qwen/Qwen2.5-Omni-7B" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Generator-blue></a>
<a href="https://huggingface.co/collections/juliozhao/doclayout-yolo-670cdec674913d9a6f77b542" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Layout-yellow></a>
<a href="https://arxiv.org/pdf" target="_blank"><img src=https://img.shields.io/badge/Paper-arXiv-red></a>


</div>

## Introduction
We introduce **TextlessRAG**, the first end-to-end framework for speech-based question answering over large-scale document images. TextlessRAG bypasses ASR, TTS, and OCR, directly interpreting spoken queries, retrieving relevant visual knowledge, and generating answers in a fully textless pipeline. 

We release the first bilingual speech–document RAG dataset **SV-DOC**, containing Chinese and English voice queries aligned with multimodal document content, to foster future research in this direction.

## 🖥️ Example
We demonstrate an example of a pipeline in the video below.

https://github.com/user-attachments/assets/27884988-2bc6-4aa2-b892-6eaa39baa005



## 🔥 News
- 🎉  We propose TextlessRAG, the first speech-based, end-to-end visual document RAG pipeline that operates without ASR, OCR, or TTS.
- 🎉  We construct SV-DOC, the first speech-based visual document RAG benchmark, featuring bilingual data in English and Chinese.
- ⏳ The project is still under ongoing development, and the code including：knowedge embedding, topk retrieval, layout reranking, QA generation will be available soon~
<!-- - ⌛️ Training code will be released soon. -->
<!-- - 🎉 Our framework integrates various embedding models, enabling you to create your own retriever.
- 🎉 We have released the ViDoSeek dataset, which is suitable for Retrieval-augmented Generation in the large visually rich document collection. -->

### List of Contents
- [x] Provide the environment setup with model weights.
- [x] Provide the details of DataEngine with Examples.
- [ ] Provide the Crops.  



## 🚀 Quick Start

### Create the Python environment.
```python
conda create -n textlessrag python=3.11.10
conda activate textlessrag
pip install git+https://github.com/illuin-tech/colpali.git #Colqwen-Omni
pip install git+https://github.com/QwenLM/Qwen2.5-Omni.git  #Qwen2.5-Omni
pip install -r requirements.txt
```
### Download CKP from Hugging Face 
Download `Retriver`，`Generator` and `LayOut` model weights from Hugging Face to folder `models`. 
| model | github | ckp |
|------|------|------|
| Colqwen-Omni | [GitHub](https://github.com/illuin-tech/colpali) | [![🤗 HF](https://img.shields.io/badge/🤗%20Hugging%20Face-orange)](https://huggingface.co/vidore/colqwen-omni-v0.1) |
| Qwen2.5-Omni | [GitHub](https://github.com/QwenLM/Qwen2.5-Omni) | [![🤗 HF](https://img.shields.io/badge/🤗%20Hugging%20Face-orange)](https://huggingface.co/Qwen/Qwen2.5-Omni-7B) |
| DocLayout-YOLO | [GitHub](https://github.com/opendatalab/DocLayout-YOLO?tab=readme-ov-file) | [![🤗 HF](https://img.shields.io/badge/🤗%20Hugging%20Face-orange)](https://huggingface.co/collections/juliozhao/doclayout-yolo-670cdec674913d9a6f77b542) |

## TextLessRAG Pipeline

<img width="500" height="350" alt="pipeline" src="https://github.com/user-attachments/assets/d6fc78bc-9838-4758-a3b0-8f1d1d93060c" />


## Data Engine

### Data Statistics

### Five-step data generation
<img width="500"  alt="data" src="https://github.com/user-attachments/assets/2ec70aa0-01ba-4197-b7aa-ab176a6203ef" />

1. Step 1:


2. Step 2:

   



### Chinese Visual Doc RAG Dataset
We construct the first Chinese Visual Doc RAG Dataset -- ChineseDocRAG(CDR)
Domains world cloud:
<img width="500" height="300" alt="wordcloud" src="https://github.com/user-attachments/assets/556408ce-8d54-41e2-9bca-a8494a8879ee" />





