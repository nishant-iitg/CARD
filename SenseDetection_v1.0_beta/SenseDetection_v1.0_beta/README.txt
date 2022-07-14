1. Package description
This Java package is developed for automatically find the centroid sense clusters for a list of clinical abbreviations from  narrative clinical notes.
The list of abbreviations can be a list of predefined abbreviations. Or, the user can generate a list of abbreviations from clinical notes using the "AbbreviationDetection" module. Given a list of abbreviations and a collection of clinical notes, this package will first extract all the sentences containing the abbreviation, then,  automatically cluster them into several group of clusters using TCRS clusering algorithm. The sentences within one clusters are supposed to have the similiar meaning. The centroid sentences for each cluster will be collected for sense annotation.
We implemented the TCRS algorithm developed in one of our previous research for sense clustering:
Xu H, Wu Y, Elhadad N, Stetson PD, Friedman C. A new clustering method for detecting rare senses of abbreviations in clinical notes. J Biomed Inform. 2012 Dec;45(6):1075-83.

Copyright: Copyright (c) School of Biomedical Informatics
Organization:The University of Texas, Health Science Center at Houston
@author Yonghui Wu


2. Usage
You can use the package from commandline:
java -jar SenseDetection_v1.0_beta.jar -i [YOUR_INPUT_FOLDER] -o [YOUR_OUTPUT_FOLDER] -av [ABBR_FILE] -mth -nth [6] -sh [SECTION_HEADER_FILE] -ac [Maximum number of abbreviation counts] -ws [FEATURE_WINDOW_SIZE]

Options:

'-i' : The input folder containing all narrative clinical notes
'-o' : The output folder 
'-av': The file containing abbreviation and its variants. Each line of the file consists of '\t' delimited two colums. The first colum is the abbreviation, the second colum is '|' delimited variants. These variants will be grouped as one abbreviation. E.g.:
pt	.pt.|pt.|PT.|Pt|pT|P.T|.Pt|.PT|.pt|.Pt.|Pt.|pt|PT

'-mth' : Whether use multithread. Optional.
'-nth' : The number of threads If use '-mth'. Optional along with '-mth'.
'-sh'  : The section header file. Each line will be treated as a section header. The section headers will be used as a feature in the sense clustering. 
'-ac'  : The maximum number of instances during the sense clustering for each abbreviation. Optional, default value is 1000.
'-ws'  : The window size for bag-of-word feature extraction. Optional, the default value is 5.

 
3.Output

CARD_sense_centroid_record.txt , A text file containing all the centroid sentences for each abbreviation. It is a '\t' delimited file, with the following format:
abbreviation '\t' abbr_id '\t' occurence_sequence in the note '\t' cluster_ids_phase1 '\t' number_of_instances '\t' Pre_processed_note

The occurence of the target abbreviation was highlighted by '##'. E.g.: 
N. Panic disorder ##with## agoraphobia	
