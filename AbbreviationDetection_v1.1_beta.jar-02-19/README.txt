1. Package description
This Java package is developed for automatically detect clinical abbreviations from narrative clinical notes.
A SVM model trained on 70 discharge summary notes from Vanderbilt hospital dischage summary notes is included in the JAR.

Copyright: Copyright (c) School of Biomedical Informatics
Organization:The University of Texas, Health Science Center at Houston
@author Yonghui Wu


2. Usage
You can use the package from commandline:
java -jar AbbreviationDetection_v1.0_beta.jar -i [YOUR_INPUT_FOLDER] -o [YOUR_OUTPUT_FOLDER] -wf [WORD_FREQENCY_FILE] [-sb]

Options:

'-i' : The input folder containing all narrative clinical notes
'-o' : The output folder 
'-wf': The word frequency file, which should be generated from a large corpus with each line formated as 'word \t normalized_frequency'.(Normalized frequency = (word frequency)/(Total # of words))
'-sb': Use this option to perform sentence boundary detection and re-organize the notes

3.Output

CARD_predict_abbrs.txt : A text file containing the list of unique abbreviations detected by CARD Abbreviation detection module.
SVM_feature.txt : The SVM feature file generate by the CARD system.
SVM_feature.txt.predict : The prediction result using CARD system.
sent : a folder containing all the notes formated with sentence boundary
