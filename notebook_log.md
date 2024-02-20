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
