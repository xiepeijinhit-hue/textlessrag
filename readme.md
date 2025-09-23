



#  <div align="center"> <img width="50" height="50" alt="learning" src="https://github.com/user-attachments/assets/bc41e430-0565-43ee-b479-095fe83c9a87" /> TextLessRAG: End-to-end Visual Document RAG by Speech without Text<div>

<div align="center">
<!-- <h1>A Multi-round Multi-modal Reinforcement Learning Framework</h1> -->
<p><strong>An end2end OCR & ASR & TTS free multimodal retrieval-augmented generation pipeline </strong></p>

<a href='https://huggingface.co/datasets/hit12345/textlessrag'><img src='https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Datasets-green'></a>
<a href="https://huggingface.co/vidore/colqwen-omni-v0.1" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Retriver-blue></a>
<a href="https://huggingface.co/Qwen/Qwen2.5-Omni-7B" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Generator-blue></a>
<a href="https://huggingface.co/collections/juliozhao/doclayout-yolo-670cdec674913d9a6f77b542" target="_blank"><img src=https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Layout-yellow></a>
<a href="https://arxiv.org/abs/2509.07538" target="_blank"><img src=https://img.shields.io/badge/Paper-arXiv-red></a>


</div>

## Introduction
We introduce **TextlessRAG**, the first end-to-end framework for speech-based question answering over large-scale document images. TextlessRAG bypasses ASR, TTS, and OCR, directly interpreting spoken queries, retrieving relevant visual knowledge, and generating answers in a fully textless pipeline. 

We release the first bilingual speech–document RAG dataset **SV-DOC**, containing Chinese and English voice queries aligned with multimodal document content, to foster future research in this direction.

## 🖥️ Example
We demonstrate an example of a pipeline in the video below.

https://github.com/user-attachments/assets/27884988-2bc6-4aa2-b892-6eaa39baa005

### Example List 
we provide examples of Chinese doc rag in [examples](dataset/CHN_examples.md) and English part in [data](dataset/readme.md)


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
- [ ] Provide the Crops of audio and document images.
- [ ] Provide the meta data.  
        



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

## 🤖 TextLessRAG Pipeline
<img width="500" height="350" alt="pipeline" src="https://github.com/user-attachments/assets/d6fc78bc-9838-4758-a3b0-8f1d1d93060c" />


### <img width="20" height="20" alt="search" src="https://github.com/user-attachments/assets/72fdf7fd-278d-42e9-98d4-18e65e048210" /> Offline knowledge embedding and layout  【todo】
Layout Dictionary
```python
id_2_class_name = {
0: 'title',
1: 'plain text',
2: 'abandon',
3: 'figure',
4: 'figure caption',
5: 'table',
6: 'table caption',
7: 'table footnote',
8: 'isolate formula',
9: 'formula caption'
}
```

### <img width="30" height="30" alt="book" src="https://github.com/user-attachments/assets/96e8fdff-ea18-40fe-8f25-6c7875f1a94d" /> Online query embedding, topk retrieval and reranking  【todo】

## 📊 Data Engine   
Details of data engine with refine rules and examples are provided in [refine rules](data.md) and [data examples](dataset/readme.md)
### Data Statistics
Among them, the chartqa, dude, infovqa, and slidevqa datasets are not the original data but filtered subsets, directly sourced from the open-source dataset in the CVPR 2025 paper VDocRAG: [https://vdocrag.github.io](https://vdocrag.github.io)

| Dataset          | Amount | Pool (pdf amount / image amount) | Content                          | Domain     |
|------------------|--------|----------------------------|----------------------------------|------------|
| chartqa          | 150    | 119                        | Chart                            | Academic   |
| dude             | 496    | 422                        | Chart / Table / Text             | Open       |
| infovqa          | 1048   | 300                        | Chart / Table / Layout / Image   | Infographic|
| slidevqa         | 760    | 657                        | Chart / Table / Image / Text     | Slide      |
| mmlongbench-doc  | 1091   | 135 / 5134                 | Chart / Table / Layout / Image / Text | Open  |
| vidoseek         | 1142   | 290 / 5349                 | Chart / Table / Layout / Image   | Open       |
| 中文bench         | 1260   | 737 / 30583                | Chart / Table / Layout / Image / Text | Open  |
| **Total**        | **5947** | **42564**                 | Chart / Table / Layout / Image / Text | Open |

### Five-step data generation
<img width="500"  alt="data" src="https://github.com/user-attachments/assets/2ec70aa0-01ba-4197-b7aa-ab176a6203ef" />

####  Step 1: Data Dollection 
We collect a diverse set of documents and reports across multiple domains and formats, including
PDFs and PPTS. 
####  Step 2: Layout
We utilize Doc-Layout YOLO to split whole page doc images into fine-grain blocks.
####  Step 3: QA Generate
The Layout blocks are processed by commercial vision–language agents(QwenVL and GPT-4o) via batch APIs to generate candidate QA pairs.
####  Step 4: Refine
The QA pairs are refined through rule-based filtering and professional human annotation.
####  Step 5: TTS
The text QA pairs are converted into speech using Doubao’s TTS API, leveraging over 200 professional voice types.
  

   
### <img width="20" height="20" alt="document" src="https://github.com/user-attachments/assets/f2932f31-5402-45f1-83c4-b3e05a842eaf" /> English Visual Doc RAG Datasets


### <img width="20" height="20" alt="google-docs" src="https://github.com/user-attachments/assets/69446942-0193-4953-85f9-d0e08d95f6f3" /> Chinese Visual Doc RAG Dataset
We construct the first Chinese Visual Doc RAG Dataset -- ChineseDocRAG(CDR)
#### <img width="15" height="15" alt="bar-chart" src="https://github.com/user-attachments/assets/25cc5ea5-8fac-4b14-a83c-f596d8246863" /> Page Distribution
<img width="4000" height="600" alt="histogram" src="https://github.com/user-attachments/assets/0bb4d5b2-c22f-44c2-add1-02c021b5c1b7" />


- Domains world cloud:

<img width="500" height="300" alt="wordcloud" src="https://github.com/user-attachments/assets/556408ce-8d54-41e2-9bca-a8494a8879ee" />

- PDF Count Across Domains

| Domain | Count |
| ---- | ---- |
| 城投&建投&城建 | 76 |
| 交通出行&运输 | 94 |
| 新能源车企 | 110 |
| 创新&创业&创客 | 52 |
| 机械设备 | 111 |
| 宏观经济&中国经济 | 115 |
| 果汁&饮料 | 131 |
| 公募REITs | 116 |
| 大健康&健康产业&健康食品 | 89 |
| 气候&环境&环保 | 81 |
| 媒体 | 137 |
| 中概互联网公司 | 23 |
| 出海 | 80 |
| 矿山&矿产&矿业 | 124 |
| 股票 | 111 |
| 财政 | 122 |
| 服装&服饰&女装&童装 | 111 |
| 低空经济 | 97 |
| 宠物&萌宠经济 | 124 |
| 小红书运营&玩法 | 109 |
| 生态 | 93 |
| 人力资源&人才招聘&薪酬&绩效 | 107 |
| 低碳 | 113 |
| 法律 | 110 |
| 大数据&大数据安全 | 125 |
| 数字化&数字化转型 | 91 |
| 销售 | 101 |
| 家居&家具&家装&全屋定制&智能家居 | 127 |
| 电子商务&直播电商&跨境电商 | 76 |
| 科技 | 58 |
| 材料 | 52 |
| 半导体&芯片 | 69 |
| 消费&新消费 | 76 |
| 软件 | 141 |
| 抖音&TikTok | 142 |
| 旅游&文旅&休闲景区 | 140 |
| 东南亚 | 127 |
| 欧洲&欧盟 | 90 |
| 生猪养殖&养猪&猪周期 | 96 |
| 船舶&航运&港口 | 123 |
| 物流&快递&智慧物流 | 93 |
| 计算机 | 92 |
| 可转债 | 109 |
| 政企&国企&央企 | 110 |
| 电池&锂电池&钠电池&动力电池 | 102 |
| 养殖业 | 72 |
| 稀土 | 83 |
| 石油化工&石化 | 143 |
| 网络安全&物联网安全&互联网安全 | 118 |
| 国产化&国产替代 | 86 |
| 公募基金 | 117 |
| 钢铁&钢材 | 120 |
| 元宇宙&虚拟现实 | 115 |
| 氢能源 | 142 |
| 全球科技公司 | 80 |
| 新材料 | 99 |
| 东数西算&算力 | 58 |
| 猎头&HR | 124 |
| 体育产业&体育行业&体育消费 | 143 |
| 利率外汇 | 100 |
| 金属铜 | 106 |
| 房地产&房贷&REITs | 101 |
| 基建行业&基础设施建设 | 107 |
| 支付行业&第三方支付&跨境支付 | 103 |
| 债券&城投债&信用债 | 90 |
| 美妆&个护&化妆品 | 123 |
| 保险 | 101 |
| 智能家电&电器&小家电 | 126 |
| 金融&绿色金融&碳金融 | 67 |
| 人工智能&ChatGPT&AIGC&生成式AI | 59 |
| 眼镜&眼科 | 115 |
| 通信 | 73 |
| 有色金属 | 66 |
| 碳交易&碳资产&碳盘查&碳市场&碳达峰&碳中和 | 112 |
| 珠宝&首饰&饰品 | 19 |
| 零售&新零售 | 82 |
| 虚拟电厂&电力系统 | 110 |
| 并购 | 119 |
| 手机用户&移动消费者 | 37 |
| 国防军工&航天装备&大飞机 | 48 |
| 智能制造 | 72 |
| 工业4.0 | 95 |
| 新质生产力 | 123 |
| 新能源汽车&充电桩 | 112 |
| 资本市场 | 111 |
| 理财&银行理财&互联网理财 | 125 |
| ESG | 109 |
| 全球资金观察系列报告 | 116 |
| 智慧养老&养老金&养老金融 | 94 |
| 制药&制药装备 | 50 |
| 机器人&家庭机器人&商用机器人&人形机器人&医疗机器人 | 68 |
| 电商购物节&双11&618 | 123 |
| 美国&美国经济民生&美国消费者 | 54 |
| 纺织品&纺织服装&家纺&棉纺织报告 | 132 |
| 日本启示录&日本经济&以日为鉴 | 87 |
| 教育&职业教育&智慧教育&在线教育&教培 | 128 |
| 短视频&直播 | 122 |
| 越南&印度&日本 | 81 |
| 航空运输&航空物流 | 83 |
| VC&PE | 134 |
| 医疗&医药 | 31 |
| 电力&风电&火电&核电 | 72 |
| 数据中心IDC | 30 |
| 消费者&人群&画像&用户 | 32 |
| 社会服务 | 141 |
| 乘用车 | 133 |
| 贵金属&黄金&白银 | 26 |
| 储能 | 110 |
| 云原生&开源&开源软件 | 72 |
| 就业 | 130 |
| 高质量发展 | 97 |
| 券商证券 | 50 |
| 金属铝 | 94 |
| 汽车 | 98 |
| 光伏&太阳


## Citation

If you use this repository in your work, please cite:

```bibtex
@misc{xie2025textlessragendtoendvisualdocument,
      title={TextlessRAG: End-to-End Visual Document RAG by Speech Without Text}, 
      author={Peijin Xie and Shun Qian and Bingquan Liu and Dexin Wang and Lin Sun and Xiangzheng Zhang},
      year={2025},
      eprint={2509.07538},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2509.07538}, 
}


