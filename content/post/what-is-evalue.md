+++
date = "2015-10-07T16:48:55-04:00"
title = "What is e-value?"
+++

A standard practice for assessing primary homology of a gene sequence is through local alignment (e.g., NCBI’s BLAST), in which an input sequence (the “query”) is matched against a particular sequence (the “hit”) in a database of sequences. The metric most commonly used to determine the significance of an alignment between a query and its hit is e-value. Given the ubiquity of this parameter, here is a short guide to explain what it is and how it’s used.

**What is e-value?**<br>
E-value (short for expect value) is a calculation of the number of sequences in the database that are expected, by chance in a random search, to align equally or more significantly to the query than the hit that was found. It reflects the frequency that you will find an equal or better match in the database for your query sequence. In effect, e-value is an estimate of the hit to have been chosen due to random background noise.

**What does the value mean, and what is the range of possible e-values?**<br>
An e-value of 1.0 means that you expect one sequence in the database to match the query as well or better than the hit you found. An e-value of 0.0 means zero sequences can/are expected to match as well or better; the closer the e-value is to zero, the more significant (and less of a potential false positive) the match is considered to be.

Although e-values can range from zero to theoretically infinity, most e-values will be a decimal between 0 and 1, represented by scientific notation (e.g., 1e-05 = 0.00001). Matches above 1.0 are most of the time not considered significant (the default cutoff for blastn, the most inclusive NCBI BLAST search, is 10.0). This does not mean that they are not potentially homologous sequences, just that a random search is expected to find multiple better candidates.

**What goes into calculating e-value?**

```E-value = K*m*n*e^(-λ*S)```

K,λ = constants based on scoring matrix; m,n = lengths of the two sequences; S = alignment score, which is calculated based on the alignment produced (incorporating matches, mismatches, gaps, etc).

Therefore, e-value is mostly dependent upon the length of the sequences, the size of the database, and the derived alignment score. This implies that shorter sequences, especially with lower complexity, are less likely to be matched significantly (and are often filtered out). Moreover, e-values derived from searches across databases of different size cannot be compared. An e-value of 6e-32 from a search against a small database is less significant than an e-value of 6e-32 from a large database; as the database grows, the likelihood of the presence of a truly homologous sequence grows in tandem, and consequently the likelihood of a false positive decreases.

**Is an e-value the thing same as a p-value?**<br>
No. E-value is a frequency metric, whereas p-value is a probability metric. Though both metrics reflect the significance of the query-hit alignment, e-value represents the number of better alignments that are expected to occur by chance, while p-value represents the likelihood that the match in question occurred by chance. (In statistical terms, the e-value is a multiple testing correction of the p-value.)

NCBI uses e-value as its standard because it provides greater clarity and granularity; “it is easier to understand the difference between, for example, e-value of 5 and 10 than p-values of 0.993 and 0.99995.” Both can be used, but be aware of which you are using and why, because they represent different things.