# biopigz :dna: :pig: :microbe:
 Fast and very sm0l bacterial genome (un)gzipper

_By Tom Stanton_ :scientist: \
[![alt text][1.1]][1] [![alt text][6.1]][6] \
Issues/queries/advice?
[email me!](mailto:s1895738@ed.ac.uk?subject=[bart])

[1]: http://twitter.com/tomstantonmicro
[1.1]: http://i.imgur.com/tXSoThF.png (twitter icon with padding)
[6]: http://www.github.com/tomdstanton
[6.1]: http://i.imgur.com/0o48UoR.png (github icon with padding)

### Introduction :open_book:
`biopigz` is a very sm0l pure-python tool for (un)gzipping bacterial genomes 
(or any other small-ish file) I wrote in response to extreme boredom
induced by incessant family Monopoly games over Christmas.

That's pretty much it.

On my Macbook M1 machine, it out-performed `pigz` when decompressing a
directory of bacterial genomes, so that's nice. Don't be surprised if it 
breaks, but if you find it useful, good on ya!

### Dependencies :toolbox:
* python >=3.9

### Usage :computer:
```sh
usage: biopigz [options] [files ...]

Input:
  files                Files to process, or stdin if none provided

Compression options:
  -d, --decompress     Decompress the compressed input (files must have the '.gz' suffix)
  -c, --stdout         Write all processed output to stdout (won't delete input files)
  -k, --keep           Do not delete original file after processing
  -l 0-9, --level 0-9  Compression level

Other options:
  -t N, --threads N    Number of threads, default: all
  --version            Show version number and exit
  -v, --verbosity      Verbosity, increases with -vv
  -h, --help           Show this help message and exit
```

 - Processes files in place, adding/removing the '.gz' suffix.
 - If stdin and not stdout, processed output will be written to `[uuid.file(.gz)]`
 - Multiple files will be processed simultaneously using `--threads`

### Examples :mag:
```sh
python3 biopigz.py -d ecoli_assemblies/*fasta.gz
```
```sh
curl https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/002/813/595/GCF_002813595.1_ASM281359v1/GCF_002813595.1_ASM281359v1_genomic.fna.gz | python3 biopigz.py -dc > GCF_002813595.1_ASM281359v1_genomic.fna
```