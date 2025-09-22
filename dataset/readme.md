#  SV-DOC Dataset
The first bilingual speech–document RAG dataset SV-DOC, containing Chinese and English voice queries aligned with multimodal document content, to foster future research in this direction.


The full dataset is currently under review and will be released once approved. To better illustrate our work, we have published 10 examples for each subset. 
## <img width="30" height="30" alt="icon_voice" src="https://github.com/user-attachments/assets/63dfbd03-555e-4ee7-bd38-146e13be9dcb" />  Audios

The spoken audio files for the Q&A were generated using Doubao’s TTS API [docs](https://www.volcengine.com/docs/6561/1257544). To ensure data generalization, we used as many different voice timbres as possible. The list of timbres involved is as follows:
- Chinese voice type list(236) in [Chinese_Voices](CHN_voices) 

- English voice type list(61) in [English_Voices](ENG_voices)


When generating speech, we randomly select a voice from the list to generate either the question or the answer. The naming convention for the audio files is:
**{q or a}@{index}@{voice\_name}.wav**
For example: *“a@[0@en\_male\_bruce\_moon\_bigtts.wav](mailto:0@en_male_bruce_moon_bigtts.wav)”*

For each dataset, we first provided 10 examples for reference, located in the directory [audio](./audio)


## <img width="20" height="20" alt="image" src="https://github.com/user-attachments/assets/e90f6dbd-b48b-4993-9ff5-3794fe7a71f1" /> Images

- For the open-source English datasets, we directly used the images they provided.
  
- For the Chinese datasets we constructed ourselves, we used PyMuPDF to convert the PDFs into PNG images at a resolution of dpi = 200.

```python
def pdf_to_images(pdf_path):
    output_dir = pdf_path.replace('/pdf/', '/png/')
    if os.path.exists(output_dir):
        return
    os.makedirs(output_dir, exist_ok=True)
    doc = fitz.open(pdf_path)
    for page_number in range(len(doc)):
        page = doc.load_page(page_number)
        pix = page.get_pixmap(dpi=200)
        image_path = os.path.join(output_dir, f"page_{page_number + 1}.png")
        pix.save(image_path)
#         print(f"save: {image_path}")
    doc.close()
```

##  <img width="20" height="20" alt="qa" src="https://github.com/user-attachments/assets/997b64c4-6b82-45c6-bcff-47a7e943a817" /> Question and Answer meta data

### English Data

#### Chartqa
```python
example={'query_id': 'chartqa-test_0',
 'query': 'Instruct: Given a user query, retrieve a chart image that answers the query.\nQuery: What percent who think of President Donald Trump as Dangerous?',
 'answers': array(['62'], dtype=object),
 'relevant_doc_ids': array(['chartqa/166.png'], dtype=object),
 'dataset_names': array(['chartqa'], dtype=object)}
```

#### DUDE
```python
example = {
'query_id': 'dude-test_0',
 'query': 'Instruct: You need to retrieve evidence from a PDF page to address the question.\nQuery: What is the minimum wage Agricultural Employees on January 1, 2020?',
 'answers': array(['$10.30'], dtype=object),
 'relevant_doc_ids': array(['dude/6fe71b02ed5e4e141a7e7a9e96505c31_0.jpg'], dtype=object),
 'dataset_names': array(['dude'], dtype=object),
}
```

#### InfoVQA
```python
example = {
'query_id': 'infovqa-test_0',
 'query': 'Instruct: Given a question, retrieve an infographic to answer the question.\nQuery: Which three business types is Pinterest good for?',
 'answers': array(['interior design, restaurants, wedding venues',
        'restaurants, wedding venues, interior design',
        'wedding venues, restaurants, interior design',
        'restaurants, interior design, wedding venues',
        'wedding venues, interior design, restaurants',
        'interior design, wedding venues, restaurants'], dtype=object),
 'relevant_doc_ids': array(['infovqa/37313.jpeg'], dtype=object),
 'dataset_names': array(['infovqa'], dtype=object),}
```

#### SlideVQA
```python
example = {
'query_id': 'slidevqa-test_0',
 'query': 'Instruct: Given a question, retrieve a slide image to answer the question.\nQuery: In which year did Nestlé achieve higher Organic Growth, 2003 or 2004?',
 'answers': array(['2003'], dtype=object),
 'relevant_doc_ids': array(['slidevqa/2012-02-20fy11roadshow-120221022442-phpapp02_95/slide_7_1024.jpg'],
       dtype=object),
 'dataset_names': array(['slidevqa'], dtype=object),}
```

#### MMLongBench-Doc
```python
example = {
'doc_id': 'PH_2016.06.08_Economy-Final.pdf',
 'doc_type': 'Research report / Introduction',
 'question': 'According to the report, how do 5% of the Latinos see economic upward mobility for their children?',
 'answer': 'Less well-off',
 'evidence_pages': '[5]',
 'evidence_sources': "['Chart']",
 'answer_format': 'Str',}
```
#### Vidoseek
```python
example ={
'uid': '03c7d62afbcc088cad1c810c09a71df29a29c968_1',
 'query': 'Apply for Nordic Swan Ecolabel license, what is recommended as a web browser according to the Nordic Ecolabelling Portal instructions?',
 'reference_answer': 'Microsoft Edge or Google Chrome.',
 'meta_info': {'file_name': '03c7d62afbcc088cad1c810c09a71df29a29c968.pdf',
  'query_type': 'single_hop',
  'reference_page': array([4]),
  'source_type': 'text'},}
```

### Chinese Data

```python
{'编号': 0,
 '领域': '城投&建投&城建',
 '问题': '2024年8月市场流传的150号文的主要内容是什么？',
 '答案': '2024年8月市场流传的150号文的主要内容包括：①隐债清零；②已剥离政府融资功能、完成市场化转型；③征得2/3债权人同意。',
 '提问对象': '政策文件',
 '提问对象类别': '流程图（包括ppt里设计的图片导图）',
 '是否合格': '是',
 'page': '城投&建投&城建/2025年02月13日更新-城投市场化转型及新增债券融资主体观察.pdf/page_1.png',
 'block': '城投&建投&城建/2025年02月13日更新-城投市场化转型及新增债券融资主体观察.pdf/page_1_Block_11_Class_3.png'},
```

