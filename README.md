# NECo
## Paper
https://www.biorxiv.org/content/10.1101/2020.06.15.149559v2
## What is NECo?
NECo is a node embedding tool that utilizes multiplex heterogeneous gene phenotype network. NECo allows multi-layer gene and phenotype networks. NECo generates gene embeddings using Gene-Gene, Gene-Phenotype and Phenotype-Gene neibhorhood spaces, using the random walk with restart rankings as node sequences.

## WMFunctions.R
Includes functions to generate the walk matrix (transition matrix) for multiplex heterogeneous network.

## RWFunctions.R
Includes functions for random walk with restart, and generation of neighborhood for each nodes in the multiplex heterogeneous network. 

## NECoFunctions.R
Includes function that generates Top N neighborhoods for Gene-Gene, Gene-Phenotype, Phenotype-Gene and Phenotype-Phenotype.

## main.R
Simple R script that provides an example of how to use NECo functions to generate different neigbhorhoods of multiplex heterogeneous network by taking input of individual networks of genes, phenotypes and bipartite network.

## GenerateNECoEmb.py
Generates NECo embeddings of genes by utilizing different neighborhoods generated by NECoFunctions.R script.

## Input Files
An input file given below is required for main.R to generate Gene-Gene, Gene-Phenotype, Phenotype-Gene and Phenotype-Phenotype neighborhoods for different top N parameters. <br>

_**type	file_name**_<br>
gene	pwy_network<br>
gene	expr_network<br>
phenotype	phenotype_net1<br>
phenotype	phenotype_net2<br>
bipartite	gene_phenotype_net<br>

Current implementation utilizes "rds" R file for network layers given below format:<br>

_**from to weight**_<br>
gene1 gene2 0.5<br>

For unweighted networks just provide 1 as weight. The related function is _read.network.layers_ in **RWFunctions.R** file to be modified for other formats.

## Usage

Run _main.R_ with modified input file and then run  _GenerateNECoEmb.py_ to generate embedding file for different neighborhood spaces. Gene embeddings of different embedding spaces then can be concatenated and utilized by a classification algorithm.
