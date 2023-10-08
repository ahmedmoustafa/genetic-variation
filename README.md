# Genetic Variation

Illumina [Platinum Genomes](https://www.illumina.com/platinumgenomes.html) is a set of whole-human genomes that were deeply sequenced by [Illumina](https://www.illumina.com/) using their [HiSeq](https://www.illumina.com/systems/sequencing-platforms/hiseq-2500.html) platform to serve as a reliable reference for genetic variation in the human genome to the scientific community. The collection is the genomes of 17 members of the [CEPH pedigree 1463](https://catalog.coriell.org/0/Sections/Collections/NIGMS/CEPHFamiliesDetail.aspx?PgId=441&fam=1463) from Utah, USA.

![CEPH pedigree 1463](https://catalog.coriell.org/0/Images/NIGMS/CEPH/1463.gif)

## Part I - Paternity Test

- [NA12878](https://www.coriell.org/0/Sections/Search/Sample_Detail.aspx?Ref=NA12878) (or GM12878) is a mother in the pedigree (person #2 in the above figure). The single-nucleotide variants (SNVs) and short variants can be found in the [Variant Call Format](https://en.wikipedia.org/wiki/Variant_Call_Format) (`.vcf`), uncompressed [`NA12878.vcf`](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/vcf/NA12878.vcf) and compressed [`NA12878.vcf.gz`](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/vcf/NA12878.vcf.gz).


- [NA12891](https://catalog.coriell.org/0/Sections/Search/Sample_Detail.aspx?Ref=NA12891) (person #15 in the above pedigree) is the father of NA12878.

- There are two [VCF files](https://github.com/ahmedmoustafa/platinum-genomes/tree/main/tsv) (simplified into `.tsv`), Unknown1 and Unknown2. One of them is NA12891, the father of NA12878.

In this part, write a Python program to predict who is NA12891, [Unknown1](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/tsv/Unknown1.tsv.gz?raw=true), or [Unknown2](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/tsv/Unknown2.tsv.gz?raw=true). Then, explain your finding and conclusion.

## Part II - SNP Density

![Human Chromosome 16](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Ideogram_human_chromosome_16.svg/474px-Ideogram_human_chromosome_16.svg.png)


In this part, write a Python program to:
1. calculate the variations (SNPs) density on chromosome 16 of NA12878's genome
2. visualize the above-calculated densities
3. identify the region on chromosome 16 with the largest number of variations
4. Are there any genes in the area you identified with the largest number of variations? You may use [The UCSC Genome Browser](https://genome.ucsc.edu/cgi-bin/hgGateway) to explore this region.

To facilitate reading and parsing the VCF file, here is a tab-separated values (`.tsv`) version, compressed [`NA12878.tsv.gz`](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/tsv/NA12878.tsv.gz?raw=true), with the needed fields for the exercise, as shown in the table below:

|       | `chr`| `pos` | `id`                         |`ref`|`alt`|
|-------|------|-------|------------------------------|-----|-----|
| 0     | chr1 | 14677 | rs201327123                  | G   | A   |
| 1     | chr1 | 15922 | rs375964566                  | A   | G   |
| 2     | chr1 | 15956 | rs112448831                  | G   | A   |
| 3     | chr1 | 16014 | rs113442401;rs75082847       | C   | T   |
| 4     | chr1 | 16298 | rs62636498;rs77798508        | C   | T   |


This includes the index column at the beginning of the table.

where,

| Field | Description |
| ----- | ----------- |
| `chr` | Chromosome  |
| `pos` | Nucleotide Position |
| `id`  | SNP accession (if known) |
| `ref` | Reference Allele |
| `alt` | Alternative Allelel |


## Hints
- Here is a [notebook](genetic_variation_notebook.ipynb) with a code snippet for loading NA12878's variants from a `tsv` file into a [`pandas`](https://pandas.pydata.org/)'s [`DataFrame`](https://www.geeksforgeeks.org/python-pandas-dataframe/)
- For the variations density analysis (Part II), consider a sliding window approach with a window size of 1000 (1K) nucleotides. You may read about the sliding window approach [here](https://www.geeksforgeeks.org/window-sliding-technique/) and [here](https://stackoverflow.com/questions/8269916/what-is-sliding-window-algorithm-examples).
- Here is a [table](https://github.com/ahmedmoustafa/platinum-genomes/blob/main/chromosomes.tsv) with the sizes of the human chromosomes.
