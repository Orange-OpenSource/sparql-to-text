# LC-QuAD 2.0 for SPARQL-to-Text

Special version of LC-QuAD 2.0 for the SPARQL-to-Text task

# New field `simplified_query`

New field is named "simplified_query". It results from applying the following step on the field "query":

* Replacing URIs with a simpler format with prefix "resource:", "property:" and "ontology:".

* Spacing the delimiters `(`, `{`, `.`, `}`, `)`.

* Adding diversity to some filters which test a number (`contains ( ?var, 'number' )` can become `contains ?var = number`

* Randomizing the variables names

* Shuffling the clauses

# New split "valid"

A validation set was randonly extracted from the test set to represent 10% of the whole dataset.

