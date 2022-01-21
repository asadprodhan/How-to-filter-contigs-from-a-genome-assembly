## **How to filter out contigs from a genome assembly file**



### **Background**


A genome assembly contains both long and short contigs. These contigs can be visualised in Bandage (Wick et al., 2015). Bandage uses the assembly graphs and displays how the contigs are connected to each other. Therefore, Bandage allows for a preliminary assessment if all these contings are part of the genome or some could be artefacts from the lab processes or the genome assembly algorithm. For example, Fig 1 is generated in Bandage using a de novo genome assembly graph (assembly.gfa). It shows that the large circular contig has 216x sequencing depth and 5.7 Mb length. On the other hand, the rest of the contigs are very short compared to the large circular contig and have a very low sequencing depth except for a few. These short contigs might not be part of the genome. However, a blast run against each contig together with the Bandage pre-assessment will be required for a robust assessment on the contigs.
<br />
<br />
 ![alt text](https://github.com/asadprodhan/How-to-filter-contigs-from-a-genome-assembly/blob/main/Genome_Assembly_in_Bandage.png)
<br />

Fig 1. A genome assembly graph visualised in Bandage. The values accompanied by ‘x’ indicate the sequencing depth; numbers followed by ‘bp’ indicate length in base pairs (bp); colours are random.
<br />
<br />


However, if any contigs need to be filtered out from the assembly file (fasta), they can be deleted manually or automated using the command line tools. Some of the command line options are presented here:
<br />
<br />
<br />
## **Filtering out by contig size**


i.	Install ‘bbmap’ package

```
conda install -c bioconda bbmap
```

ii.	Run the following command: 

```
reformat.sh in=AssemblyFile.fasta out=AssemblyFile_Filtered.fasta minlength=200
```

>‘reformat.sh’ is a built-in bash scrip in the ‘bbmap’ package
>
>‘in’ is the name of the input assembly file
>
>‘out’ is the name of the filtered assembly file
<br />
<br />

## **Filtering out by contig name**


i. Again, it uses the ‘bbmap’ package and can be installed as follows:

```
conda install -c bioconda bbmap
```

ii.	Run the following command: 

```
filterbyname.sh in= AssemblyFile.fasta out= AssemblyFile_Filtered.fasta  names=List_of_names.txt exclude
```

>‘filterbyname.sh’ is a built-in bash scrip in the ‘bbmap’ package
>
>‘in’ is the name of the input assembly file
>
>‘out’ is the name of the filtered assembly file
>
>‘names=names.txt’ contains one name per line. These are the contigs that will be excluded or included based on what is specified next
>‘exclude’ will exclude the contigs listed in the ‘names=names.txt’
>
>‘include=t’ will keep the contigs listed in the ‘names=names.txt’ and discard the rest
<br />
<br />

### Reference

Wick, R. R., Schultz, M. B., Zobel, J., & Holt, K. E. (2015). Bandage: Interactive visualization of de novo genome assemblies. Bioinformatics, 31(20), 3350–3352. https://doi.org/10.1093/bioinformatics/btv383

