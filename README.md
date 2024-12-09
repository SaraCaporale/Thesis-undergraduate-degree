# Thesis-undergraduate-degree

> The implementation code is found in the [submodule](https://github.com/SaraCaporale/PFP-eBWT). \
> The document array (DA) construction's implementation corresponding to the eBWT can be found as code additions in all repository files [here](https://github.com/SaraCaporale/PFP-eBWT/commit/a8c2eabad520b9cba52cbdda5b1f1183f0aa7f87). \
> The `distances.cpp` file contains the computation of the distances based on the eBWT and DA.

## Thesis 

Study of the prefix-free parsing for the comparison of biological sequences via eBWT \
Università di Pisa, Corso di Laurea Triennale in Informatica \
Supervisors: [Giovanna Rosone](https://github.com/giovannarosone), [Veronica Guerrini](https://github.com/veronicaguerrini) \
Candidate: Sara Caporale \
Date: 11/10/2024

## Abstract

In recent years, the size of genomic databases has increased significantly due to the progress of bioinformatics research.

A key area of interest in this context is sequence comparison, which aims to identify structural, functional and evolutionary relationships among organisms as represented by their genomes. To this end, many similarity and dissimilarity measures have been defined in order to capture the similarities and differences between genomic sequences. 

By computing pairwise proximity measurse on a collection of sequences, it is possible to construct the corresponding distance matrix. These matrices can be used to generate phylogenetic trees, diagrams that graphically represent the relationships among organisms represented by their genomic sequences. Such trees show the evolutionary history of a set of organisms and their hypothetical common ancestry.

In order to deal with the scale of genomic databases, it has become important to use fast and efficient data structures. One of the most widely used structures is the index, with many popular indexes being based on the _Burrows-Wheeler Transform_ (BWT). The BWT produces a permutation of the original text where identical characters are usually grouped together, making it easier to compress the data. The BWT is also reversible, i.e. knowing the permutation and the index in the BWT of the first character, the original text can be reconstructed.

The computation of the BWT has been extended to a collection of strings in [6], and it has been called _extended Burrows Wheeler Transform_ (eBWT).

Various techniques have been proposed to build the BWT and eBWT. One of the most recent ones is called _prefix-free parsing_ (PFP), and it aims to reduce the cost of computation both in time and space. This technique has been introduced for the construction of the BWT [1] [2], but it has been extended for the eBWT in [8]. In this work we carry out a study on the algorithm for building the eBWT via PFP. PFP is a dictionary-based approach that parses the input, builds the eBWT of the parse and builds the eBWT of the original input using the dictionary, the parse, and the eBWT of the parse.

To the original implementation of the PFP for eBWT, this work integrates the computation of the _document array_ (DA), an auxiliary data structure that identifies the string from which each character of the eBWT comes. 

In some applications, such as data compression, when inverting the eBWT it is important to retrieve the strings in the same order as they were provided in input. In this implementation we build a small data structure that allows us to invert the eBWT and obtain the strings preserving the order in which they appear in the original collection.

Thanks to the properties of the eBWT and leveraging the document array, many proximity measures have been proposed. In this work, we study the dissimilarity measures introduced in [5] [6] [7]. The basic idea is that similar sequences are likely to share identical text segments. This means that the higher the frequency of shared segments, the more characters from different strings will alternate in the eBWT and, consequently, in the DA.

In this work we conduct some experiments on four genomic datasets: _Escherichia coli_, _HIV-1_, _Drosophila_, mitochondrial DNA of cichlid fishes. For each of them, we build the eBWT via PFP and the corresponding DA. We compute the distance matrix for each dissimilarity measure and we generate the corresponding phylogenetic tree. For each dataset we show the tree known in the literature and we compare it with those obtained.

# References

[1] Christina Boucher, Travis Gagie, Alan Kuhnle and Giovanni Manzini: *Prefix-Free Parsing for Building Big BWTs.* In Proc. of the 18th International Workshop on Algorithms in Bioinformatics, WABI 2018.

[2] Christina Boucher, Travis Gagie, Alan Kuhnle, Ben Langmead, Giovanni Manzini and Taher Mun: *Prefix-free parsing for building big BWTs.* Algorithms Mol. Biol. 14(1): 13:1-13:15 (2019)

[3] Ge Nong, Sen Zhang and Wai Hong Chan: *Two Efficient Algorithms for Linear Time Suffix Array Construction.* IEEE Trans. Computers 60(10): 1471-1484 (2011)

[4] Hideo Bannai, Juha Kärkkäinen, Dominik Köppl and Marcin Piatkowski: *Constructing the bijective and the extended Burrows-Wheeler-Transform in linear time.* In Proc. of the 32nd Annual Symposium on Combinatorial Pattern Matching, CPM 2021.

[5] S Mantaci et al. “A New Combinatorial Approach to Sequence Comparison”. In: Theory of Computing Systems 42.3 (apr. 2008), pp. 411–429.

[6] Sabrina Mantaci et al. “An Extension of the Burrows Wheeler Transform and Applications to Sequence Comparison and Data Compression”. In: Combinatorial Pattern Matching. A cura di Alberto Apostolico, Maxime Crochemore e Kunsoo Park. Berlin, Heidelberg: Springer Berlin Heidelberg, 2005, pp. 178–189. isbn: 978-3-540-31562-9.

[7] Lianping Yang, Xiangde Zhang e Tianming Wang. “The Burrows–Wheeler similarity distribution between biological sequences based on Burrows–Wheeler transform”. In: Journal of Theoretical Biology 262.4 (2010), pp. 742–749. issn: 0022-5193. doi: https://doi.org/10.1016/j.jtbi.2009.10.033. url: https://www.sciencedirect.com/science/article/pii/S0022519309005220.

[8] Christina Boucher et al. “Computing the Original eBWT Faster, Simpler, and with Less Memory”. In: Proceedings of 28th International Symposium in String Processing and Information Retrieval SPIRE 2021. Vol. 12944. Lecture Notes in Computer Science. 2021, pp. 129–142.
