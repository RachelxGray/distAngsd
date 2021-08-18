# distAngsd
## Descriptions
<strong>distAngsd</strong> is a software to simulate and infer phylogenetic relationships between two individuals, in which two novel methods (i.e., geno and nuc) are proposed. A bunch of other methods are also implemented, e.g., RandomSEQ, ConsensusSEQ and ConsensusGT for comparisons. The software can both conduct simulation and analyses real vcf/bcf file given reliable genotype likelihoods are calculated.

The software can do 1-d simulation and inference (only genetic distance <em>t</em> estimation), 2-d simulation and inference (only genetic distance <em>t</em> and invariable sites proportion <em>p_inv</em> estimation), vcf file read and inference. Both JC69 are GTR models can be considered. Genotype likelihood and inference logs can be recored either in the format of txt.gz or bin.

The codes are put in the Codes folder which currently contains Makefile, io.cpp, bfgs.cpp, GLtest.cpp, GL2Dtest.cpp, ExistingMethods.cpp vcftest.cpp, GL-Reads.cpp, io.h, bfgs.h, GLtest.h, GL2Dtest.h, ExistingMethods.h vcftest.h, and GL-Reads.h.
## Compilation and Run
### Compilation
make distAngsd
### Run
./distAngsd -o -method -model -glf -vcf -simrep -is2Dinfer -p_inv -isthreading -dobinary -numsites -isuchar -RD -errorrate -tdiv -t1 -t2 -par

One and only one following two options must be provided to specify whether to infer based on simulation or vcf file.
* -vcf specifies the directory of input vcf files.

* -simrep specifies the number of simulation replicates.

* -o specifies the recorded logs which contain command detail and inferred results for either simulation/real vcf files. The default value is <em>distAngsdlog</em>. Such log files will always be provided.

* -method can be either JC or GTR. The default value is <em>JC</em>.

* -glf specifies the directory of output genotype likelihoods files. If -glf is not provided, genotype likelihoods files will not be saved. 

* -is2Dinfer determines whether genetic distance t and invariable site proportion p_inv are jointly inferred. The default value is 0, which means, by default, only genetic distance t will be inferred on the assumption that all sites are variable.

* -p_inv gives the simulated true p_inv. It should be provided if a 2-d simulation and inference is conducted.

* -isthreading determines whether the EM algorithm is conducted parallelly

* -dobinary determines whether the output files is saved as .bin or .txt.gz

* -numsites is the number of sites in simuation

* -isuchar determines whether store the real genotype likelihoods in a more compressed unsinged char format

* -RD is the average read depth for simulation

* -errorrate is the base calling error for simulation

* -tdiv is the true divergence time (genetic distance) for simulation

* -t1 -t2 are defined as manuscript

* -par gives comma-delimited 9 parameters (first 5 for symmetric matrix and last 4 for stationary distribution) for GTR model, and the last 4 as a distribution will be normalised automatically.
