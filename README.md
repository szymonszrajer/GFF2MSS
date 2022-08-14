# Automatised GFF to MSS conversion
--final script and documentation are under construction--
file conversion inspired by GFF2MSS by Taro Maeda


Most, if not every annotation software used nowadays generates GFF files to describe genes and other features of sequences. This creates an issue, as none of the INSDC databases (DDBJ, ENA, NCBI) accepts annotations submitted in that format yet.

In the project that resulted in this program, we chose DDBJ for a submission of the *Gryllus Bimacaulatus* genome annotation. Such submission required for conversion from GFF format to DDBJ-native, MSS format. 

Files generated by annotation software contain errors which stem from imperfection of current annotation software. To look for the errors within the annotation file we used two validation programs distributed by the DDBJ, transChecker and jParser (https://www.ddbj.nig.ac.jp/ddbj/ume-e.html). Ways of resolving errors that were present in our annotation file were incorporated to the AutomatisedGFFtoMSSconversion program. 






