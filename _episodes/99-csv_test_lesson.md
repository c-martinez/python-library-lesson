---
title: "Reading a .csv file using the csv module in Python"
teaching: 5
exercises: 10
questions:
- "How can I read a csv file using Python, search for a result and save it?"
objectives:
- "Be able to read a csv file, run a command and save the results in a new csv file"
---

## Let's start by learning how to read the csv file. 
* How should we approach this algorithmically? 
* We want to:
	* tell python to import csv module so python knows how to parse this type of file
	* open the file so python can read the file
	* then read each row and print it out


~~~
import csv

#open csv file
with open('data/doaj-article-sample.csv', 'r') as file: 

	csv_data = csv.reader(file)

	#reading the header title and printing it
	header_row = next(csv_data)
	print(header_row)

	#reading each row of the data file
	for row in csv_data: 
		print(row)

~~~
{: .python}
~~~
['Title', 'Authors', 'DOI', 'URL', 'Date', 'Language', 'Subjects', 'ISSNs', 'Publisher', 'Citation', 'Licence']
['The Fisher Thermodynamics of Quasi-Probabilities', 'Flavia Pennini|Angelo Plastino', '10.3390/e17127853', 'https://doaj.org/article/b75e8d5cca3f46cbbd63e91be5b32412', '01/11/2015', 'English', 'Fisher information|quasi-probabilities|complementarity|Physics|QC1-999|Science|Q', '1099-4300', 'MDPI AG', 'Entropy, Vol 17, Iss 12, Pp 7848-7858 (2015)', 'CC BY']
['Aflatoxin Contamination of the Milk Supply: A Pakistan Perspective', 'Naveed Aslam|Peter C. Wynn', '10.3390/agriculture5041172', 'https://doaj.org/article/0edc5af6672641c0bd45608812a34f9e', '01/11/2015', 'English', 'aflatoxins|AFM1|AFB1|milk marketing chains|hepatocellular carcinoma|Agriculture (General)|S1-972|Agriculture|S', '2077-0472', 'MDPI AG', 'Agriculture (Basel), Vol 5, Iss 4, Pp 1172-1182 (2015)', 'CC BY']
['Metagenomic Analysis of Upwelling-Affected Brazilian Coastal Seawater Reveals Sequence Domains of Type I PKS and Modular NRPS', 'Rafael R. C. Cuadrat|Juliano C. Cury|Alberto M. R. Dávila', '10.3390/ijms161226101', 'https://doaj.org/article/d9fe469f75a0442382b84ba4f50007ee', '01/11/2015', 'English', 'PKS|NRPS|metagenomics|environmental genomics|upwelling|coastal environment|Chemistry|QD1-999|Science|Q', '1422-0067', 'MDPI AG', 'International Journal of Molecular Sciences, Vol 16, Iss 12, Pp 28285-28295 (2015)', 'CC BY']
['Synthesis and Reactivity of a Cerium(III) Scorpionate Complex Containing a Redox Non-Innocent 2,2′-Bipyridine Ligand', 'Fabrizio Ortu|Hao Zhu|Marie-Emmanuelle Boulon|David P. Mills', '10.3390/inorganics3040534', 'https://doaj.org/article/95606ed39deb4f43b96f7e6308ad15d3', '01/11/2015', 'EN', 'lanthanide|cerium|scorpionate|tris(pyrazolyl)borate|radical|redox non-innocent|Inorganic chemistry|QD146-197', '2304-6740', 'MDPI AG', 'Inorganics (Basel), Vol 3, Iss 4, Pp 534-553 (2015)', 'CC BY']

etc.
~~~
{: .output}

## Let's add an if statment to see how many times a certain author name shows up in the file. 

*  	Every row in this example is considered a list in Python. 
*	To search for a specific column, we can look at where the element is located. In this example, Author is the 2nd column, so we can search that column by typing in row[1]. In Python, we count starting at 0 for lists. 
* For string types, we can check if certain characters exist in a given string with the operator 'in'. 

~~~
import csv


#open csv file
with open('data/doaj-article-sample.csv', 'r') as file: 

	csv_data = csv.reader(file)

	#reading the header title and printing it
	header_row = next(csv_data)
	print(header_row)

	#reading each row of the data file
	for row in csv_data: 
	#to find the authors column, we will access the 2nd item on the row list
	#we are searching for the author name of 
		if 'Hyunjin Park' in row[1]:
			print row
		else:
			continue

~~~
{: .python}
~~~
['Crystal structure of flumioxazin', 'Hyunjin Park|Jineun Kim|Eunjin Kwon|Tae Ho Kim', '10.1107/S2056989015017223', 'https://doaj.org/article/957c5641016242949fd1ba7170482249', '01/10/2015', 'EN', 'crystal structure|dicarboximide herbicide|flumioxazin|1H-isoindole|1,4-benzoxazine|C—H...F hydrogen bonds|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 10, Pp o768-o768 (2015)', 'CC BY']
['Crystal structure of mandipropamid', 'Hyunjin Park|Jineun Kim|Gihaeng Kang|Tae Ho Kim', '10.1107/S2056989015016643', 'https://doaj.org/article/7fd2628136e54a2488680aa3316f3e94', '01/10/2015', 'EN', 'crystal structure|conformation|hydrogen bonding|C—H...π interactions|amide fungicide|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 10, Pp o727-o728 (2015)', 'CC BY']
['Crystal structure of fenbuconazole', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S205698901501542X', 'https://doaj.org/article/90988a785293428a9c57d6a151ec05a6', '01/09/2015', 'EN', 'crystal structure|fungicide|fenbuconazole|C—Cl...π interactions|π–π interactions|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 9, Pp o680-o681 (2015)', 'CC BY']
['Crystal structure of cafenstrole', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S2056989015013869', 'https://doaj.org/article/070a0f64de3a44aa856452836b25abe0', '01/08/2015', 'EN', 'crystal structure|cafenstrole|triazole|herbicide,|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 8, Pp o614-o614 (2015)', 'CC BY']
['Crystal structure of nuarimol', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S2056989015013493', 'https://doaj.org/article/eac7e1f997bc44ae99558af197396e23', '01/08/2015', 'EN', 'crystal structure|nuarimol|pyrimidine fungicide|hydrogen bonding|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 8, Pp o586-o587 (2015)', 'CC BY']
['Crystal structure of pyriproxyfen', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S2056989015013481', 'https://doaj.org/article/eb30d6c9e2d44f18bcfb99d36afda391', '01/08/2015', 'EN', 'crystal structure|pyriproxyfen|ether|juvenile hormone mimic|insecticide|π–π stacking|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 8, Pp o588-o588 (2015)', 'CC BY']
['Crystal structure of the enol form of mesotrione: a benzoylcyclohexanedione herbicide', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S2056989015012803', 'https://doaj.org/article/89a119acde8641aca4c511cb4a6929b1', '01/08/2015', 'EN', 'crystal structure|tautomerization|enol form|intramolecular O—H...O hydrogen bond.|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 8, Pp o548-o549 (2015)', 'CC BY']
['Crystal structure of oxadiargyl', 'Gihaeng Kang|Jineun Kim|Hyunjin Park|Tae Ho Kim', '10.1107/S2056989015011524', 'https://doaj.org/article/b998908e67db4bb1bc0ff95081159d7b', '01/07/2015', 'EN', 'crystal structure|oxadiargyl|1,3,4-oxadiazolone|herbicide|hydrogen bonding|Cl...Cl short contacts|Chemistry|QD1-999', '2056-9890', 'International Union of Crystallography', 'Acta Crystallographica Section E: Crystallographic Communications, Vol 71, Iss 7, Pp o494-o494 (2015)', 'CC BY'] 	
~~~
{: .output}

## Let's now modify the code so that we can save our results in a new csv file. 

*   By saving the results in a new csv file, we can return to the results later, or use this new file to do more data manipulation. 

~~~
import csv

#This opens the file to write 
output_file = open('data/doaj-article-author-results.csv', 'w')

#Creating a writer object with the file we just opened
writer = csv.writer(output_file, delimiter=',')

#opens csv file that we want to read: 
with open('data/doaj-article-sample.csv', 'r') as file: 
	csv_data = csv.reader(file)

	#reading the header title and printing it
	header_row = next(csv_data)
	print(header_row)

	#writing the header titles to our output file
	writer.writerow(header_row)
	
	#reading each row of the data file
	for row in csv_data: 
	#to find the authors column, we will access the 2nd item on the row list
	#If the authors column has an author with the name 'Hyunjin Park' we will write this result to teh new file
		if 'Hyunjin Park' in row[1]:
			writer.writerow(row)
			print(row)
		else:
			continue
	#closing file we were writing to
	output_file.close()
	

~~~
{: .python}
~~~
* Check out your data folder, it should have a file named doaj-article-author-results.csv with the results. 
