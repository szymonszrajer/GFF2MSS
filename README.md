# Automatised GFF to MSS conversion
file conversion inspired by GFF2MSS by Taro Maeda
https://github.com/maedat/GFF2MSS

Most, if not every annotation software used nowadays generates GFF files to describe genes and other features of sequences. This creates an issue, as none of the INSDC databases (DDBJ, ENA, NCBI) accepts annotations submitted in that format yet.

In the project that resulted in this program, we chose DDBJ for a submission of the *Gryllus Bimacaulatus* genome annotation. Such submission required for conversion from GFF format to DDBJ-native, MSS format. 

Files generated by annotation software contain errors which stem from imperfection of the current annotation software. To look for the errors within the annotation file we used two validation programs distributed by the DDBJ, transChecker and jParser (https://www.ddbj.nig.ac.jp/ddbj/ume-e.html). Ways of resolving errors that were present in our annotation file were incorporated to the AutomatisedGFFtoMSSconversion program. 

The program contains two scripts:

AutomatisedGFFtoMSS.py - performs GFF to MSS file conversion.
AutomatisedGFFtoMSSPart2.py - fixes errors raised by transchecker and prepares file for jParser validation.

General pipeline when converting GFF for submission looks like this:

''' bash 
# Call the first script
python AutomatisedGFFtoMSS.py input1.gff input2.fasta DNA Homo_sapiens - Japan > mss_file.ann
'''

''' bash
# Call transchecker
transChecker.sh -xmss_file.ann -sinput2.fasta -etransChecker_errors.txt
'''

''' bash
# Call the second script
python AutomatisedGFFtoMSSPart2.py transChecker_errors.txt mss_file.ann ABCDE
'''

''' bash
# Call jParser for validation
jParser.sh -xmms_file.ann -sinput2.fasta
'''

The finished script by no means covers all of the exceptions that can be present in a mss file and need to be fixed before submission.
The attached script, called duplicates.py can be used if warnings regarding duplicates are present in the final jParser output.



