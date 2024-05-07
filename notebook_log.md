Notebook-log for Phylogenetics – Final Version 

Accessing Phytophthora and Pythium populations in soybean fields in the state of Wisconsin

* Pythium and Phytophthora are microorganisms that resemble fungi and are often referred to as water mold since they need water for life-cycle completion. These microorganisms can survive in the soil for many years and under the right environmental conditions (flooded soil and warmer temperatures) they can develop and infect soybean roots. Although these pathogens infect the soybeans primarily when the plants are in the seedling stages, they can cause disease during the whole plant cycle. The symptoms can be secondary root bruises, yellowing leaves, dark brown lesions on the stem, and even complete plant death. 

* Because these pathogens are highly destructive and can cause severe damage to soybean production, is very important that we know the species and pathotype (in the case of Phytopthora sojae) of these genera present in the state so we can address the right management tool against these pathogens and protect the soybean yield. 

* For this reason, one of the main goals of the project is to assess the population of these oomycetes and their geographical distribution in Wisconsin to provide a better understanding of their behavior and the correct management tools available against them. 

* To accomplish our goal, in the past two seasons, we received around 400 soil samples from soybean fields throughout the main producer regions in WI. After deploying techniques to bait Pythium and Pytophthora and molecular assays to extract their genetic material we obtained around 300 DNA samples that were sent to sequencing (SANGER sequencing) using the primers ITS 6 (forward) and ITS 4 (reverse).

First Part – Assembling my sequences.

For the year 2023, I successfully collected 310 sequences that will be used for the Phylogenetic tree (in the future I will incorporate my 2024 isolate’s sequences). 

•	The DNA samples were sent to be SANGER sequences using ITS 6 (forward primer) and ITS 4 (reverse primer). The results were received in ab1 files, I used the paid version of the software Geneious Prime to perform the assembling and alignment. I uploaded all the ab1 files to a folder called “Alignment” on the Geneious Prime software main page. 

•	To decide if the sequences could be used for my project, I looked at the quality of the sequence, if both sequences of one sample (forward and reverse) were superior to 87% (personal choice) I would proceed to assemble them. Otherwise, if less than 87%, I discarded them from my collection. 

•	If I proceeded to use the I would trim the poor-quality edges of all the samples. To do so, I allowed editing of the sequence on the buttons “allow editing”, “annotate and predict “, and “Trim ends”.  This popped a new window to display the trimming options. On this new window, I selected the following settings for all the used sequences and pressed ok.

“Annotate new trimmed regions.”
“Error probability limit: 0.01”
“Trim 5` End at last (I left the “at last” part empty)”
“Trim 3` End at last (I left the “at last” part empty)”


•	After trimming the ends, I proceeded to assemble the forward and the reverse sequences to create a consensus sequence file. To do so I opened the tool “align/assemble” on the tool options at the top of the page and selected “De Novo Assemble” option. This opened a new window where I selected the following settings and pressed ok. 

“Dissolve contigs and re-assemble.”
“Assembler: TadPole” 
“Sensitivity: Medium Sensitivity/Fast”
“Assembly name: #for the name I put the name of my isolate.”
“Save assembly report.”
“Save consensus sequences.”

P.S.: The TadPole kmer-based assembler, with additional capabilities of error-correcting and extending reads. Compared to most other assemblers, it is incredibly fast, has a very low misassembly rate, and is very adept at handling extremely irregular or super high coverage distributions.

•	The outcome from the steps above was 155 consensus sequences of the forward and reverse primers that were then used for the alignment of multiple sequences. I selected all the consensus sequences displayed on the “Alignment” folder created on the main screen of Geneious Prime and proceeded with the alignment. I selected the “Alignment/Assemble” tool again but then chose the “Multiple Align…” option. A new window popped up, where I made the following selections and pressed ok (after pressing ok it will run the alignment and notice that this can take a while depending on how many sequences will be aligned).

“MUSCLE Alignment” #This uses the Muscle 5.1 by Robert C. Edgar
“Algorithm PPP”

P.S. 2: MUSCLE stands for MUltiple Sequence Comparison by Log-Expectation. MUSCLE is claimed to achieve both better average accuracy and better speed than ClustalW2 or T-Coffee.

•	After running the steps above, it will automatically create a new file called “Nucleotide alignment”. I select this file and go to the “File” option on the top of my screen, put my mouse on “Export”, then “Documents”, this pops a new window that allows you to choose what format to export the alignment file to my laptop. For my project, I used the NEXUS and FASTA format. I proceeded to save this file in the same folder I have my IQ-tree reproducible file. 

Alignment file information: I aligned 155 consensus files that had various lengths from 417 to 1,011 bp. The final alignment was obtained using MUSCLE and had a 1,399 bp length. It was saved in a NEXUS and FASTA format under the name “oomycete_alignment.nex” and “oomycete_alignment.fasta” in the path: “/Users/sarahsouza/Downloads/iqtree-2.3.2-macOS-intel/bin/ oomycete_alignment.nex” and “/Users/sarahsouza/Downloads/iqtree-2.3.2-macOS-intel/bin/ oomycete_alignment.fasta”

Second Part – Creating a Neighbor-Joining Tree. 

To create a tree based on the pairwise distance, I first created a tree using the NJ algorithm which is known to be fairly accurate and faster. However, distance methods reduce the phylogenetic information to one value per pair of sequences, so many times regarded as inferior compared to character-based methods (less stat power due to the loss of info). 

•	The tree was created in RStudio (version 2023.09.1+494) using the “adegenet”, “phangorn”, and  “ape” packages, followed by the commands below”

“# To install the necessary packages:
install.packages(“ape)”

“# To load the necessary packages:
library(ape)”

“# To load my data:
oomycete <- fasta2DNAbin(file="/Users/sarahsouza/Downloads/iqtree-2.3.2-macOS-intel/bin/ oomycete_alignment.fasta")

“# To compute the genetic distances using Tamura and Net 1993.
distance_oomycete <- dist.dna(oomycete, model="TN93")”

“#To get the Neighbor-Joining Tree:
nj_tree <- nj(distance_oomycete)”

“# To plot the tree”
plot(nj_tree, 
main="Pythium and Phytophthora genera Phylogenetic tree",
cex=0.2)”

Third Part – Creating an IQ Tree. 

•	IQ-Tree is a fast and effective stochastic algorithm to infer phylogenetic trees by maximum likelihood, it combines elements of hill-climbing algorithms, random perturbation of current best trees , and a broad sampling of initial starting trees. It claims higher likelihoods are achieved relative to RAxML and PhyML.

•	With the saved Nexus file saved on the same folder as my IQ-tree executor, I can now create a second tree using the command line IQ-tree “software”. 

•	On my terminal, I can proceed to go to the file in which IQ Tree and the nexus files are saved. Using the following commands: 

“cd Downloads”
“cd iqtree-2.3.2-macOS-intel”
“cd bin”
“ls                                  
iqtree2					oomycete2_alingment.fasta.mldist
oomycete2_alingment.fasta.bionj		oomycete2_alingment.fasta.model.gz
oomycete2_alingment.fasta.ckp.gz	oomycete2_alingment.fasta.treefile
oomycete2_alingment.fasta.iqtree	sarah_oomycete_allignment.nex
oomycete2_alingment.fasta.log     oomycete_alignment.nex

•	In this directory, I can now run the code to create my tree:

“./iqtree2 -s oomycete_alignment.nex”

•	This command will start running and show the likelihood calculations for the trees. This step can also take a while depending on how big the alignment is and how many taxa I have. 

•	After running it will give me the output of the analysis and the nex.iqtree, nex.treefile, and the nex.log. The last one will present me the information about the best tree found. I will use the .treefile to create a presentable tree using RStudio. 


IQ-Tree information: The tree created for my data using IQ-Tree presented an optimal log-likelihood and best score found of -14427.901. The base frequencies were A: 0.208; C: 0.193; G: 0.277; and T: 0.322. The total tree length was 11.156 and 560 total interactions. Best-fit model: TN+F+I+R5 chosen according to BIC.

•	Using the following codes from the ape package in RStudio I was able to create the tree from the “oomycete_alignment.nex.iqtree” saved on the same folder as my IQ-tree executor. 

“# To install and load the ape package:
install.packages("ape")
library(ape)"

"# To load your tree from the .tree file
tree <- read.tree("/Users/sarahsouza/Downloads/iqtree-2.3.2-macOS-intel/bin/oomycete_alignment.nex.treefile")"

# To plot the tree

"plot(tree,
           main="Pythium and Phytophthora genera Phylogenetic tree",
           show.tip.label = TRUE, 
           cex = .2)"

