# SPARQL-to-Text Question Generation

SPARQL-to-Text question generation refers to the task of converting a SPARQL query into a natural language question, eg:

```SQL
SELECT (COUNT(?country) as ?answer)
WHERE  { ?country property:member_of resource:Europe .
                ?country property:population ?n .
                FILTER ( ?n > 10000000 )
              }
```

could be converted into:

```txt
How many European countries have more than 10 million inhabitants?
```

---

## Content of the repository

This repository contains:

* **5 prepared and homogenized for the SPARQL-to-Text question generation task:**

  > ⚠ **_NOTE:_**  Datasets are now stored on https://huggingface.co/OrangeInnov.
  
  - Non conversational datasets
    - SimpleQuestions (from https://github.com/askplatypus/wikidata-simplequestions)
    - ParaQA (from https://github.com/barshana-banerjee/ParaQA)
    - LC-QuAD 2.0 (from http://lc-quad.sda.tech/)
  - Conversational datasets
    - CSQA (from https://amritasaha1812.github.io/CSQA/)
    - WebNLQ-QA (derived from https://gitlab.com/shimorina/webnlg-dataset/-/tree/master/release_v3.0)

* **A T5 and BART models trained on all datasets**
  > ⚠ **_NOTE:_**  Models are now stored on https://huggingface.co/OrangeInnov.
  - *Base version* from 🤗 HuggingFace (https://huggingface.co/t5-base and https://huggingface.co/facebook/bart-base)
  - Input format is `<context> Conversational context alternating user and system utterances </context> <query> Your SPARQL query </query> <answer> Expected answer(s) </answer>`, eg:
  ```xml
  <context> <user> Was anybody born in Reşadiye? <system> No <system> What about in Zaoyang? <user> Yes <user> Who is it? <system> Nie Haisheng </context> <query> SELECT DISTINCT ( COUNT ( ?t ) AS ?e ) WHERE { resource:Nie_Haisheng property:mission ?t } </query> <answer> 2 </answer>
  ```  
  - If some fields are unavailable (eg. answer is unknown), they can be skipped
* **Predictions made by:**
  - the T5 model with context and answer
  - the T5 model where context and answer are replaced by a short parargraph from which the answer could be guessed
  - A naive template-based model

## Licence

The original content of each dataset is under distinct licences described below (as provided by their original creators):
* CSQA : CC BY-SA 4.0
* LC-QuAD 2.0 : CC BY 3.0
* ParaQA : CC BY 4.0
* SimpleQuestions : CC-BY 3.0
* WebNLG version 3.0: CC-BY-SA 4.0

Augmented annotations and predictions provided in this repository are published under the licence CC BY-SA 4.0.

The models are published under the licence Apache 2.0, as the models are taken from 🤗 HuggingFace.


## Citation

```bibtex
@inproceedings{lecorve2022sparql2text,
  title={SPARQL-to-Text Question Generation for Knowledge-Based Conversational Applications},
  author={Lecorv\'e, Gw\'enol\'e and Veyret, Morgan and Brabant, Quentin and Rojas-Barahona, Lina M.},
  journal={Proceedings of the Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the International Joint Conference on Natural Language Processing (AACL-IJCNLP)},
  year={2022}
}
```


