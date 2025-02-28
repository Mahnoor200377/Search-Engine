# Search-Engine
### Overview
In this assignment, you will write an indexer and use it to index a collection of documents. In the
next assignment, you will create a ranker that uses your index to process queries. If you combine
these two assignments, you will have constructed a simple search engine.
You will write three programs:
- A tokenizer, which reads a document collection and creates documents containing
indexable tokens
- An indexer, which reads a collection of tokenized documents and constructs an inverted
index
- A tool which reads your index and prints information read from it

### Part 1: Tokenizing Documents
The first step in creating an index is tokenization. You must convert a document into a stream of
tokens suitable for indexing. Your tokenizer should follow these steps:
- Accept a directory name as a command line argument, and process all files found in that
directory
- Extract the document text with a parsing library, ignoring the headers at the beginning of
the file and all HTML tags if any
- Split the text into tokens
- Apply stop-wording to the document by ignoring any tokens found in this list (Stopword
list will be provided)
- Apply stemming to the document using any standard algorithm. You can use a stemming
toolkit for this (UNLT https://eprints.lancs.ac.uk/id/eprint/165032/).
- Your tokenizer will write three files:
o docids.txt – A file mapping a document's filename (without path) to a unique
integer, its DOCID. Each line should be formatted with a DOCID and filename
separated by a tab, as follows:
1234\doc123
o termids.txt – A file mapping a token found during tokenization to a unique
integer, its TERMID. Each line should be formatted with a TERMID and token
separated by a tab, as follows:
567\tasparagus
o doc_index.txt – A forward index containing the position of each term in each file.
One line of this file contains all the positions of a single token in a single
document. Each line should contain a DOCID, a TERMID, and a list of all the
positions of that term in that document (the first term has position 1, the second
has position 2, etc.). The DOCID, TERMID, and positions should be separated by
