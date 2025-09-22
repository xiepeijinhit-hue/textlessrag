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

##  <img width="20" height="20" alt="qa" src="https://github.com/user-attachments/assets/997b64c4-6b82-45c6-bcff-47a7e943a817" /> Question and Answer meta data

### English Data

#### Chartqa
```
example={'query_id': 'chartqa-test_0',
 'query': 'Instruct: Given a user query, retrieve a chart image that answers the query.\nQuery: What percent who think of President Donald Trump as Dangerous?',
 'answers': array(['62'], dtype=object),
 'relevant_doc_ids': array(['chartqa/166.png'], dtype=object),
 'dataset_names': array(['chartqa'], dtype=object)}
```

#### DUDE

#### InfoVQA

#### SlideVQA

#### MMLongBench-Doc

#### Vidoseek

### Chinese Data


