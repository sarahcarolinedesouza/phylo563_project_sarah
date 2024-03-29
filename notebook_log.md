Accessing Phytophthora and Pythium populations in soybean fields in the state of Wisconsin

* Pythium and Phytophthora are microorganisms that resemble fungi and are often referred to as water mold since they need water for life-cycle completion. These microorganisms can survive in the soil for many years and under the right environmental conditions (flooded soil and warmer temperatures) they can develop and infect soybean roots. Although these pathogens infect the soybeans primarily when the plants are in the seedling stages, they can cause disease during the whole plant cycle. The symptoms can be secondary root bruises, yellowing leaves, dark brown lesions on the stem, and even complete plant death. 

* Because these pathogens are highly destructive and can cause severe damage to soybean production, is very important that we know the species and pathotype (in the case of Phytopthora sojae) of these genera present in the state so we can address the right management tool against these pathogens and protect the soybean yield. 

* For this reason, one of the main goals of the project is to assess the population of these oomycetes and their geographical distribution in Wisconsin to provide a better understanding of their behavior and the correct management tools available against them. 

* To accomplish our goal, in the past two seasons, we received around 400 soil samples from soybean fields throughout the main producer regions in WI. After deploying techniques to bait Pythium and Pytophthora and molecular assays to extract their genetic material we obtained around 300 DNA samples that were sent to sequencing (SANGER sequencing) using the primers ITS 6 (forward) and ITS 4 (reverse). 

 
* Currently, we do not have all the sample sequences but as soon as these data are collected we will proceed to perform the quality control steps with FastQC on the raw files and then use the software Geneious Prime for set paired reads of the forward and reverse, trim the edges of both sequences using BBDUK, and finally, perform an aligning/assembly of the sequences using De Novo Assemble. 

* Similar work was already made previously in different states (Rojas et al., 2017; McCoy et al., 2022) and will be used as a reference. The scripts used by Rojas et al. 2016 for data treatment and analysis, provided on (https://github.com/Chilverslab/Rojas_Survey_Phytopath_2016) will also be used as reference during the current project.



February 20th, 2024 - Details for homework: Aligning my data 


* As for today, I sequenced around 200 samples using the ITS 4 and 6. I used the software Ingenious to assemble both strains into one consensus strain. I will the consensus use to identify the species in the NCBI public database and proceed with the alignment to further tree building. 

* So far, I have around 20 different species identified, and therefore, this is the number of species and sequences I will work through my project (the number will probably increase or decrease as I progress through my research). 
 
* Because of technical issues downloading and installing ClustalW and MUSCLE, I will use default T-Coffee to align my DNA sequences. 

* To proceed with the alignment I will copy all the consensus sequences for the different species from the Ingenious software I used to assemble using the FASTA format (this format can be read by T-Coffee) in a text file and save it as "oomyceteAA.txt". 

* After that and assuming that T-Coffee is properly installed on my laptop (still working on some technical issues), I can open the terminal and run the following code: 


"(base) sarahsouza@Sarahs-MacBook-Air ~ % t_coffee "oomyceteAA.txt"."


* I tried to run the code but unfortunately, my terminal output is an error that says t_coffee command was not found, even though it is already installed and I already created a path to the command as I was oriented by online video tutorials. 

* Future to do: I need to solve this issue so I can actually run the code. 


March 5th, 2024 - Details for homework

Because of technical issues, I wasn't able to align my data yet so I cannot run the codes using my actual data. However, once I get the data I will run both of the following codes using R:

The NJ tree
"{R}: 
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)

library(ape)
library(adegenet)
library(phangorn)

dna <- fasta2DNAbin(file="put my data address")

D <- dist.dna(dna, model="TN93") #Tamura and Nei 1993 model which allows for different rates of transitions and transversions, heterogeneous base frequencies, and between-site variation of the substitution rate.

tre <- nj(D)

tre <- ladderize(tre)

plot(tre, cex=.6)
title("A simple NJ tree")"


The Parsimony method
"{R}: 
install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)

library(ape)
library(adegenet)
library(phangorn)

dna <- fasta2DNAbin(file="put my data address")

## read as phangorn object:
dna2 <- as.phyDat(dna)

tre.ini <- nj(dist.dna(dna,model="raw"))
parsimony(tre.ini, dna2)

tre.pars <- optim.parsimony(tre.ini, dna2)

plot(tre.pars, cex=0.6)"

Future to do: run the alignment method to align my data and try to run the above codes for my tree. 

3/21/2024 - Choosing a maximum likelihood method that you like the best on your project dataset (it does not have to be RAxML or IQ-Tree)

* As for today, I finished all my sequences, resulting in 240 viable sequences and around 20 different species of Oomycete. However,  not all these sequences I was able to retrieve a consensus, so for now I am working on aligning the sequences I was able to get a consensus then I can download the FASTA format to move forward with the alignment. 

* Because of the technical issues with downloading the alignment tools, I will use the software Geneious Prime to proceed with the alignment. This software has the MUSCLE alignment available, which is the method I will use to align my dataset. This tool allows a progressive alignment strategy, initially constructing a guide tree based on pairwise sequence similarities using a distance matrix. Then, it will run a series of pairwise alignments, progressively aligning sequences based on the guide tree. The algorithm then processes the alignment by maximizing a score based on a log-expectation function, considering the probabilities of observing the aligned residues in related sequences. 

p.s. 1: I ran the alignment as an experiment with a smaller dataset to check and the software seemed to retrieve a good alignment.

p.s. 2: Once I am going through the alignment process I will write the commands and all the details of what I am doing to get to that alignment and log in on my notebook_log.md to keep track of my steps and allow reproducibility in the future. 

* Unexpectedly, I sequenced an unrelated fungal species. I will use this sequence as well to align along with my dataset to use it for future rooting of the tree. 

* Once I have the alignment data I can perform the tree. I will not use Geneious Prime to build my tree (although the software gives us that possibility). My dataset is not big or extensive so I could use either of the maximum likelihood methods (RAxML or IQ-Tree) to build it. However, after the paper discussions in our class, I will most likely choose IQ-Tree based on the fact that I am a little more familiar with this method and the updated version seems to give as lot of very useful and "more modern" tools.

p.s.: this choice may change in the future based on any technical difficulties on installing or using it. 


