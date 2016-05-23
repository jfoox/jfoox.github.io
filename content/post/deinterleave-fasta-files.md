+++
date = "2015-09-06T10:12:48-04:00"
icon = "/img/python.png"
title = "A simple script to deinterleave FASTA files"
+++
One wall I run up against constantly when doing bioinformatics is dealing with interleaved FASTA files. Whether it has to do with aligning sequences, splitting up large files, or retrieving sequences, I often find myself wanting to take interleaved FASTA files and deinterleave them such that entire sequences are on one line. Fortunately, this is easily fixed with a simple Python script:

<script src="https://gist.github.com/jfoox/ea3228f9d39725e82a126a64d06baccf.js"></script>

...in which an interleaved FASTA file is read, and exported line by line — either with surrounding carriage returns, in the case of an identifier line, or without any carriage returns, which unites sequence lines that contain carriage returns at the end of lines in the original file. (The variable **linenum** is included to eschew the leading carriage return in case of the first sequence, such that the generated file does not begin with an empty line.)

Run this script on the command line like so:

```python deinterleave.py <your_file.fa>```

And you’ve got a new deinterleaved FASTA file in seconds! Happy coding!