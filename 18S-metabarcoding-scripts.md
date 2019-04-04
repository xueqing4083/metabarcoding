## Bioinformatics scripts used for mock metabarocding analyses
## All commands executed in QIIME v1.9.1

## SILVA reference database files downloaded from https://www.arb-silva.de/no_cache/download/archive/qiime/


## Pick open-reference OTUs

#### V1/V2

pick_open_reference_otus.py -r SILVA_132_QIIME_release/rep_set/rep_set_18S_only/99/silva_132_99_18S.fna -i input-FASTA-seqs-V1V2-390bp.fasta -o 18S-rRNA-mock-metabarcoding-V1V2-390bp -p 18S_openref99_rdp_silva132.txt -s 0.10 --prefilter_percent_id 0.0 --suppress_align_and_tree

#### V8/V9

pick_open_reference_otus.py -r /macqiime/SILVA_132_QIIME_release/rep_set/rep_set_18S_only/99/silva_132_99_18S.fna -i input-FASTA-seqs-V8V9-380bp.fasta -o 18S-rRNA-mock-metabarcoding-V8V9-380bp -p 18S_openref99_rdp_silva132.txt -s 0.10 --prefilter_percent_id 0.0 --suppress_align_and_tree 

## Make BIOM OTU tables with metadata

biom add-metadata -i otu_table_mc2.biom --observation-metadata-fp rep_set_tax_assignments.txt -o otu_table_mc2_w_uclust-tax_metadata.biom --sc-separated taxonomy --observation-header OTUID,taxonomy -m rRNA-polymorphism-qiime-mapping.txt


## Convert BIOM tables to tab-delimited text 

biom convert -i otu_table_mc2_w_tax.biom -o otu_table_mc2_w_tax.txt --table-type "OTU table" --to-tsv --output-metadata-id=taxonomy --header-key=taxonomy


