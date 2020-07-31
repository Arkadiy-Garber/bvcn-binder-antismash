# Binder for BVCN AntiSMASH lesson

Initially forked from [here](https://github.com/binder-examples/conda). Thank you to the awesome [binder](https://mybinder.org/) team!

[![Binder](https://mybinder.org/badge_logo.svg)](https://gesis.mybinder.org/binder/v2/gh/Arkadiy-Garber/bvcn-binder-antismash/master?urlpath=lab)

Part of the [Bioinformatics Virtual Coordination Network](https://biovcnet.github.io/) :)


## Walkthrough

Download antismash databases

    download-antismash-databases

Print the antismash help menu

    antismash -h

Run the simplest version of the command

    antismash Sodalis_praecaptivus-fixed.gbk

Run the simplest version of the command with an assembly

    antismash --genefinding-tool prodigal Sodalis_praecaptivus-fixed.fasta

Print full help menu

    antismash --help-showall

go into the wspgenie output directory and check out the output file

    antismash --genefinding-tool prodigal --fullhmmer --pfam2go --asf --cb-knownclusters Sodalis_praecaptivus-fixed.fasta

check out the gene predictions

    cd ORF_calls/
    cd ../../

mv ORF calls to the main directory

    mv wspgenie_out/ORF_calls/ ./

print LithoGenie help menu

    MagicLamp.py LithoGenie -h

run LithoGenie on ORF calls

    MagicLamp.py LithoGenie -bin_dir ORF_calls/ -bin_ext faa --orfs -out lithogenie_out

check out the output

    cd lithogenie_out/
    less -S lithogenie-summary.csv
    less lithogenie.ALL.heatmap.csv
    cd ../

re-run LithoGenie to create a .heatmap.csv for an element-of-interest

    MagicLamp.py LithoGenie -bin_dir ORF_calls/ -bin_ext faa --orfs -out lithogenie_out --skip -cat sulfur
    # answer 'y' to the question
    MagicLamp.py LithoGenie -bin_dir ORF_calls/ -bin_ext faa --orfs -out lithogenie_out --skip -cat iron

check out the new results

    cd lithogenie_out/
    less lithogenie.sulfur.heatmap.csv
    less lithogenie.iron.heatmap.csv

print the HmmGenie help menu

    MagicLamp.py HmmGenie -h

run HmmGenie with a set of HMMs for gas vesicle formation

    MagicLamp.py HmmGenie -hmm_dir MagicCave/hmms/gas/ -hmm_ext hmm -bin_dir test_dataset/ -bin_ext fna -out gas_out

check out the results and re-run HmmGenie with more stringent parameters

    MagicLamp.py HmmGenie -hmm_dir MagicCave/hmms/gas/ -hmm_ext hmm -bin_dir test_dataset/ -bin_ext fna -out gas_out -clu 5

check out the results

    cd gas_out/
    less -S genie-summary.csv

