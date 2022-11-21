# Paraqa Sparql2text

Special version of SimpleQuestions with SPARQL queries formatted for the SPARQL-to-Text task

# JSON fields

The original version of SimpleQuestions is a raw text file listing triples and the natural language question. A JSON version has been generated and augmented with the following fields:

* `rdf_subject`, `rdf_property`, `rdf_object`: triple in the Wikidata format (IDs)

* `nl_subject`, `nl_property`, `nl_object`: triple with labels retrieved from Wikidata. Some entities do not have labels, they are labelled as `UNDEFINED_LABEL`

* `sparql_query`: SPARQL query with Wikidata IDs

* `verbalized_sparql_query`: SPARQL query with labels

* `original_nl_question`: original natural language question from SimpleQuestions. This is in **lower case**.

* `recased_nl_question`: Version of `original_nl_question` where the named entities have been automatically recased based on the labels of the entities.

# Format of the SPARQL queries

* Randomizing the variables names

* Delimiters are spaced

# Answerable/unanserable

Some questions in SimpleQuestions cannot be answered. Hence, it originally comes with 2 versions for the train/valid/test sets: one with all entries, another with the answerable questions only.

