# CSQA for SPARQL-to-Text

CSQA corpus (Complex Sequential Question-Answering) augmented with various fields to make it easier to run specific tasks, especially SPARQL-to-text conversion.

The original data has been post-processing as follows:

1. Verbalization templates were applied on the answers and their entities were verbalized (replaced by their label in Wikidata)

2. Questions were parsed using the CARTON algorithm to produce a sequence of action in a specific grammar

3. Sequence of actions were mapped to SPARQL queries and entities were verbalized (replaced by their label in Wikidata)


# Storage

The corpus follows the global architecture from the original version of CSQA (https://amritasaha1812.github.io/CSQA/).

There is one directory of the train, dev, and test sets, respectively.

Dialogues are stored in separate directories, 100 dialogues per directory.

Finally, each dialogue is stored in a JSON file as a list of turns.

# JSON fields

Each turn of a dialogue contains the following fields:

## Original fields

* `ques_type_id`: ID corresponding to the question utterance

* `description`: Description of type of question

* `relations`: ID's of predicates used in the utterance

* `entities_in_utterance`: ID's of entities used in the question

* `speaker`: The nature of speaker: `SYSTEM` or `USER`

* `utterance`: The utterance: either the question, clarification or response

* `active_set`: A regular expression which identifies the entity set of answer list

* `all_entities`: List of ALL entities which constitute the answer of the question

* `question-type`: Type of question (broad types used for evaluation as given in the original authors' paper)

* `type_list`: List containing entity IDs of all entity parents used in the question

## New fields

* `is_spurious`: introduced by CARTON, 

* `is_incomplete`: either the question is self-sufficient (complete) or it relies on information given by the previous turns (incomplete)

* `parsed_active_set`: 

* `gold_actions`: sequence of ACTIONs as returned by CARTON

* `sparql_query`: SPARQL query

## Verbalized fields

Fields with `verbalized` in their name are verbalized versions of another fields, ie IDs were replaced by actual words/labels.

# Format of the SPARQL queries

* Clauses are in random order

* Variables names are represented as random letters. The letters change from one turn to another.

* Delimiters are spaced

# References

## Original paper (CSQA)

```
@InProceedings{saha2018complex,
	title = {Complex {Sequential} {Question} {Answering}: {Towards} {Learning} to {Converse} {Over} {Linked} {Question} {Answer} {Pairs} with a {Knowledge} {Graph}},
	volume = {32},
	issn = {2374-3468},
	url = {https://ojs.aaai.org/index.php/AAAI/article/view/11332},
	booktitle = {Proceedings of the AAAI Conference on Artificial Intelligence},
	author = {Saha, Amrita and Pahuja, Vardaan and Khapra, Mitesh and Sankaranarayanan, Karthik and Chandar, Sarath},
	month = apr,
	year = {2018}
}
```

## CARTON

```
@InProceedings{plepi2021context,
	author="Plepi, Joan and Kacupaj, Endri and Singh, Kuldeep and Thakkar, Harsh and Lehmann, Jens",
	editor="Verborgh, Ruben and Hose, Katja and Paulheim, Heiko and Champin, Pierre-Antoine and Maleshkova, Maria and Corcho, Oscar and Ristoski, Petar and Alam, Mehwish",
	title="Context Transformer with Stacked Pointer Networks for Conversational Question Answering over Knowledge Graphs",
	booktitle="Proceedings of The Semantic Web",
	year="2021",
	publisher="Springer International Publishing",
	pages="356--371",
	isbn="978-3-030-77385-4"
}
```

## SPARQL queries

```
@misc{lecorve2022sparql,
	author={Lecorv\'e, Gw\'enol\'e and Veyret, Morgan and Brabant, Quentin and Rojas, Lina M.},
	title={SPARQL-to-Text Question Generation for Knowledge-Based Conversational Applications},
	year={2022}
}
```


