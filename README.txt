Installation and execution of AntEpiSeeker2.0

1.Compile:
On Linux systems: GNU Scientific Library (GSL) should be installed before compiling. Compile the program using "g++ AntEpiSeeker.cpp -o AntEpiSeeker -lgsl -lgslcblas" and run the program using "./AntEpiSeeker".

On windows systems: GNU Scientific Library (GSL) files "libgsl.dll","libslcblas.dll" and "WinGsl.dll" should be put in the same folder with AntEpiSeeker as well as your system folder (e.g., "c:\windows\system32"). Compile the program using a C++ compiler.

2.Input Format
The user should create a tab-delimited file which contains the case-control genotype data as an input for the program. The first row of this input file contains the sample status (0 or 1). The following rows are the genotype data which should be coded by 0, 1 and 2 with each row corresponding to one SNP. For example,

class 1 1 1 0 0
rs1 0 1 1 2 2
rs2 1 2 0 1 2
rs3 2 2 1 2 1
rs4 2 2 1 1 2

The user should also make a tab-delimited file which contains information of pathway-SNP associations. Each pathway should be placed in one row, with the first column specifying the pathway ID and the following columns containing its associated SNPs. For example,

pw1 rs1 rs2 rs3
pw2 rs4 rs5
pw3 rs6 rs7 rs8 rs9

A complete testing dataset is available at http://lambchop.ads.uga.edu/AntEpiSeeker2_testing_data.zip.

3.Parameter file
The parameters for running AntEpiSeeker are specified in the "parameters.txt" file. These parameters include iAntCount, iItCountHsize, alpha, iTopModel, iTopLoci, rou, phe, largesetsize, smallsetsize, iEpiModel, pvalue, pwprop, PWSNPFL, INPFILE, OUTFILE and PWYFILE.

The parameter "iEpiModel" specifies the number of SNPs in an epistatic interaction. The parameters "largesetsize", "smallsetsize" must be greater than "iEpiModel". For two-locus interaction model, we suggest largesetsize=6, smallsetsize=3, iEpiMode=2; For three-locus interaction model, we suggest largesetsize=6, smallsetsize=4, iEpiModel=3.

The parameter "iItCountHsize" should be chosen according to the number of SNPs genotyped in the data. Typically, we suggest iItCountHsize=200 for <=100000 SNPs and iItCountHsize=1000 for >100000 SNPs.

4.Output
Four output files will be generated by AntEpiSeeker. "AntEpiSeeker.log" under the AntEpiSeeker directory records the intermediate results including the detected top ranked SNP sets and the loci with top pheromone levels. "results_maximized.txt" records all detected epistatic interactions meeting the pre-defined P-value threshold. The OUTFILE and PWYFILE specified by the user in the parameter file report the detected epistatic interactions with minimized false positives and sorted pathways according to pheromones respectively.

5.Support
Questions and comments should be directed to Yupeng Wang (wyp1125@gmail.com).
