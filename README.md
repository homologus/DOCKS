# DOCKS

These codes are developed by Yaron Orenstein, David Pellow, Guillaume Marcais, Ron Shamir and Cal Kingsford.
They were originally posted [here](http://acgt.cs.tau.ac.il/docks/). 
The authors made the code freely available under GNU Lesser General Public License, version 3, or any later 
version at your choice.

Here is a copy and paste of the README file from [authors' site](http://acgt.cs.tau.ac.il/docks/) -

## DOCKS - Design of Compact K-mer Set for hash functions

DOCKS (short for Design of Compact K-mer Sets for hash functions) is a software for finding a compact set of k-mers that hits every L-long sequence. DOCKS takes as input a list of parameters and outputs a list of k-mers. Further details on the functionality of DOCKS are available in the paper listed below.
DOCKS was developed by Yaron Orenstein, David Pellow, Guillaume Marcais, Ron Shamir and Cal Kingsford.

Get the software

[decycling.jar](http://acgt.cs.tau.ac.il/docks/decycling.jar)

[DOCKS.jar](http://acgt.cs.tau.ac.il/docks/DOCKS.jar)

[code.zip](http://acgt.cs.tau.ac.il/docks/code.zip)

This distribution is our officially supported executable for DOCKS. These binary are mostly self-contained and should work out of the box without any issues. For Integer Linear Programming solver (ILP) DOCKS uses Gurobi solver.

The software is freely available under the GNU Lesser General Public License, version 3, or any later version at your choice.

DOCKS is a research tool, still in the development stage. Hence, it is not presented as error-free, accurate, complete, useful, suitable for any specific application or free from any infringement of any rights. The Software is licensed AS IS, entirely at the user's own risk.

How to generate decycling set

~~~~~~~~~
java -jar decycling.jar <output file> <k> <Alphabet>
~~~~~~~~~

Example run:

~~~~~~~~~
java -jar decycling.jar decycling_5_ACGT.txt 5 ACGT
~~~~~~~~~

This command will genearte a decycling set for k=5 over ACGT alphabet. The output will be saved to decycling_5_ACGT.txt.

How to find additional k-mers to hit all L-long sequences

~~~~~~~~~
java -jar DOCKS.jar <output file> <input decycling file> <k> <L - sequence length> <Alphabet> <ILP time limit> <0/1/2/3 - random/greedyL/greedyAny/none> <x - optional with any>
~~~~~~~~~

Example DOCKS run:

~~~~~~~~~
java -jar DOCKS.jar res_5_20_ACGT_0_1.txt decycling_5_ACGT.txt 5 20 ACGT 0 1
~~~~~~~~~

Example DOCKSAny run:

~~~~~~~~~
java -jar DOCKS.jar res_5_20_ACGT_0_2.txt decycling_5_ACGT.txt 5 20 ACGT 0 2
~~~~~~~~~

Example DOCKSAnyX (X=125) run:

~~~~~~~~~
java -jar DOCKS.jar res_5_20_ACGT_0_2_125.txt decycling_5_ACGT.txt 5 20 ACGT 0 2 125
~~~~~~~~~

In all of the runs, the use needs to provide the decycling set computed by decycling.jar.

Example ILP run (limited to 1000s), with no DOCKS solution:

~~~~~~~~~
java -jar DOCKS.jar res_5_20_ACGT_1000_3.txt decycling_5_ACGT.txt 5 20 ACGT 1000 3
~~~~~~~~~

You may need to use more memory for higher values of k, i.e. k>=10, by adding -Xmx4096m option for example.
You may need to increase heapspace size for random mode for DFS, by adding -Xss515m option for example.

Interpreting the output

decycling's and DOCKS's outputs should look like this:
~~~~~~~~~
AAAACAAA
AAAAGAAA
AAAATAAA
AAACCAAA
...
ATAACGAA
TCACCGAA
GCCTACTA
TCCTCCTA
~~~~~~~~~
Each line is a k-mer in the set.

Pre-computed decycling sets

[Decycling sets for ACGT alphabet 5 <= k <= 15](http://acgt.cs.tau.ac.il/docks/decycling.zip)

Pre-computed universal (k,L) sets

[Universal hitting k-mer sets for 5 <= k <= 10, 20 <= L <= 200](http://acgt.cs.tau.ac.il/docks/ukl_k_5_10_L_20_200.zip)

[Universal hitting k-mer sets for k=11 20 <= L <= 200](http://acgt.cs.tau.ac.il/docks/res_11.zip)

[Universal hitting k-mer sets for k=12 20 <= L <= 200 computed by DOCKSany](http://acgt.cs.tau.ac.il/docks/res_12_20-200_ACGT_5_1.zip)

[Universal hitting k-mer sets for k=13 20 <= L <= 200 computed by DOCKSany1000](http://acgt.cs.tau.ac.il/docks/res_13_20-200_ACGT_5_1000.zip)

## Citing DOCKS

DOCKS can be cited as follows:
[Compact universal k-mer sets](http://acgt.cs.tau.ac.il/papers/David_P_compact_universal_k-mer_hitting_sets.pdf)
Yaron Orenstein, David Pellow, Guillaume Marcais, Ron Shamir and Carl Kingsford.
WABI 2016.
Journal version submitted.

In case of any questions or suggestions please feel free to contact Yaron Orenstein.


