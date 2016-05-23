+++
date = "2015-09-08T16:53:34-04:00"
icon = "/img/python.png"
title = "How to retrieve a set of sequences from within a FASTA file with Python"
+++
A common need in bioinformatics is to extract a subset of sequences from within a FASTA file. You might only want sequences from a particular taxon, sequences that were matched in a BLAST search, sequences that you chose by throwing a dart on a map of South America — the reasons are endless. Imagining a file with five nucleotide sequences labeled Seq1-Seq5, and that you only want odd numbered sequences, like so:

| **Original**            | **Desired**   | **Output**              |
| ----------------------- |:-------------:| -----------------------:|
| >Seq1                   | Seq1          | >Seq1                   | 
| ACTGCGTATCGACTAGCTA ... | Seq3          | ACTGCGTATCGACTAGCTA ... |
| >Seq2                   | Seq4          | >Seq3                   |
|TACTATATCAGTGTCGCGT ...  |               | ATGATATGTCGGCCGGTTG ... |
|>Seq3                    |               | >Seq4                   |
|ATGATATGTCGGCCGGTTG ...  |               | GTATTGATGCATCAGTCGT ... |
|>Seq4                    |
|GTATTGATGCATCAGTCGT ...  |
|>Seq5                    |
|AATGCGTAAGTAGTCGCGT ...  |

Once more, Python to the rescue! Create a separate text file with the identifier names of interest (like the second column above), and their extraction can be achieved quickly and easily with the following script:

<script src="https://gist.github.com/jfoox/3bdeabc263de32f98dd49cabb130fb8b.js"></script>

Run on command line:

```python seqretriever.py <your_file.fa> <desired_sequences> <desired_output_name> ```

Lines 9-22 create a temporary deinterleaved version of your FASTA file, except with identifiers and sequences on one line rather than two. This is done so they can easily be populated into a dictionary **all_seqs** on lines 25-29. The set of desired sequences **desired_seqs** is created on lines 32-35 by pulling from an external file of sequence names.
 
The keys (identifiers) within **all_seqs** are then searched for overlap with **desired_seqs**, and the overlapping names are entered into toextract on lines 38-40. These are used to pull out desired sequences (which are stored as values of the identifier keys) from all_seqs, which are exported into the final justdesired FASTA file on lines 42-44.

Note that we are using sets — unordered collections of unique elements. Because sets do not record order of insertion, the order of the output cannot be controlled, and will likely be different than the order of input. We do this because detecting overlap between sets and dictionaries is much faster than scanning iterable sequences/lists. The former is an O(1) algorithm, meaning its computational time is independent of the size of the dataset, whereas the latter is O(N), meaning its computational time is linearly proportional to the size of the dataset. As you can imagine, once your dataset becomes large enough (e.g., FASTA files with tens of thousands of sequences), you will always want to find a no-growth algorithmic solution! Sets and dictionaries are great solutions for this kind of rapid membership/overlap testing. Happy coding!

