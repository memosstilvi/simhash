##Simhash made simple

####A simple python module that calculates calculates the Simhash value of documents.

Simhash is a hashing technique that belongs to the LSH (Local Sensitive Hashing) algorithmic family.
It was initially developed by Moses S. Charikar in 2002 and is described in detail in his [paper] (http://www.cs.princeton.edu/courses/archive/spring04/cos598B/bib/CharikarEstim.pdf).
The main goal of this algorithm is to detect near duplicate documents, since similar documents will most probably 
have similar (or even the same) simhash value.
A straightforward explanation of the Simhash algorithm can be found [here] (http://matpalm.com/resemblance/simhash/).

###How it works

The unique and most interesting characteristic of the Simhash algorithm is that near duplicate documents will most likely 
have the same (or pretty similar) hash value. This feature makes it very useful when it comes to near duplicate document detection 
since it doesn’t require to compare all the documents with each other. That comparison would result to a O(n^2) complexity.
By using simhash we no longer need a pair-wise comparison between all the documents. We only need a single pass over our collection. 
After calculating the hash values for all the documents we just need to compare the ones that share the same (or similar) hash values which results in an O(n) complexity.

More specifically, in order to calculate the simhash value of a document we perform the following steps:

1. Split the document in tokens (words, characters or n-grams)
2. Hash each token separately using MD5
3. Calculate the bit representation of this MD5 hashes
4. Calculate and apply a weight to each of the document’s tokens. In our case this weights are the term frequencies in the document.
5. Merge the bit representations of all the tokens of the document in order to calculate the document’s final hash value.

###Quick Use (from stdin)

`cat YOUR_DOC | python simhash.py`

###License

Distributed under the MIT license. See `LICENSE` for more information.
