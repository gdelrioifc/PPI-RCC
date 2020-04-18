# PPI-RCC
Supplementary material for the publication entitled "Protein-Protein interactions efficiently modeled by residue cluster classes" by Albros Hermes Poot Velez, Fernando Fontove and Gabriel Del Rio

This repository contains 8 directories.

First is the directory with the supplementary graphics of the Figure 7:

	i) positive_negative_ppi: 16 figures with the comparison of positives and negative PPI through RCC. 
    The names of the files indicate the construction method used as follows: distance criterion of 7 or 8 Å, 
    with (yesSC) o without (noSC) side chain, sum (sum = 26 features) or concatenation (con = 52 features) of RCCs. 
    The statistical significance were measured with Wilcoxon test corrected by Bonferroni (bonfer) or 
    FDR Benjamini-Hochberg (fdrbh) (p<0.05). The X-axis shows the RCC feature (RCC1, RCC2...RCC26 or RCC52), 
    and the Y-axis the class of RCC and corresponding values that are compared.

The second folder contains the testing sets used:

	ii) testing_sets: The 24 testing sets used for this work in arff format.

The following folders contain the algorithms resulting of the training sets, compressed with XZ Utils:

	iii) training_models_compressed_norm_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset normalized and a distance criterion of 7 Å.

	iv) training_models_compressed_norm_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset normalized and a distance criterion of 8 Å.

	v) training_models_compressed_raw_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset raw and a distance criterion of 7 Å.

	vi) training_models_compressed_raw_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset raw and a distance criterion of 8 Å.

	vii) training_models_compressed_stand_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset standardized and a distance criterion of 7 Å.

	viii) training_models_compressed_stand_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset standardized and a distance criterion of 8 Å.

All these models were generated with <a href="https://www.cs.waikato.ac.nz/ml/weka/">Weka</a>, a freely available implementation in Java language for machine learning methods.

After decompressing the training_models, to test these algorithms we provide the corresponding testing_set. For this mean, the first 3 fields on each file (separated by underscore), are the same between testing (ii) and training files (iii-viii). 

The following is an example of the the code to test the algorithms:

	java -Xmx{MEML}m -cp {AUTOWEKA} {CLASS} -T {TES} -l {MOD} > {OUT}

In which the terms between braces are replaced as follow (without the braces):

	MEML = The limit memory to use for executing the java virtual machine
	AUTOWEKA = /The/path/to/Auto-WEKA/autoweka.jar file 
	CLASS = The WEKA class: 'weka.classifiers.meta.AutoWEKAClassifier'
	TES = The testing_set_file.arff
	MOD = The corresponding training_model_file.mod 
	OUT = Optional. The file in which the output will be redirected, otherwise it will be sent to the standard output



The names of the files describes the conditions used to build the corresponding RCCs. Below is a summary scheme of the names in the RCC column:

	{norm/stand/raw}_{7/8}{no/yes}SC_{con/sum}_{training/testing}_under_sz{1/2/3}_it{1/2/3}(_over{200/300})

The fields are separated by an underscore. The first field {stand/norm/raw} specifies if the RCC were standardize, normalized or taken without further modification; The digits of the second field {7/8} indicates the distance in Angstroms used to build the contact map; {no/yes}SC inform if side-chain atoms were used or not in the construction of the contact map. The third field {con/sum} describe if concatenation or addition of each RCC for a protein-protein pair was implemented. The fourth field {training/testing} refers to the data set being part of the training or the testing process. From the Fifth to the seventh field is the information of the undersampling procedure used, the sz{1/2/3} refers to the proportion of the undersampling of the majority class (positive) with reference to the length of the minority class (negative), as follows: sz1 = undersampling 1:1, sz2 = undersampling 2:1 and sz3 = undersampling 3:1 of positives (P) vs negatives (N) respectively; the seventh field it{1/2/3} refers to the random iteration seed used for the undersampling. Last, the 8 field (_over{200/300}) may or not be present, it is the indicative of the oversampling sets, which all part from an undersampling 1:1 set. In this way, the negative class was synthetically oversampled to generate the same 1:2 (over200), or twice the quantity of negative instances 1:3 (over300) (P:N).



Abbreviations:

	RCC = Residue Cluster Class
	PPI = Protein-Protein interaction
	P = positive PPI pairs of proteins
	N = negative PPI pairs of proteins
	norm = normalization used in the construction of the training or testing data sets
	stand = standardization used in the construction of the training or testing data sets
	raw = data used as is in the training or testing set
	7 = distance of 7 Å used to generate the contact map
	8 = distance of 8 Å used to generate the contact map
	noSC = without side chain
	yesSC = with side chain
	con = concatenation of RCCs
	sum = sum of RCCs
	under = undersampling
	sz1 = undersampling 1:1 (P:N)
	sz2 = undersampling 2:1 (P:N)
	sz3 = undersampling 3:1 (P:N)
	it1, it2 or it3 = the random iteration seed used for the undersampling
	over200 = the synthetic oversampling used to generate twice negative instances than positive one 1:2 (P:N)
	over300 = the synthetic oversampling used to generate three times more negative instances than positive ones 1:3 (P:N)
	In these last two cases, a copy of the original negative set was included, thus only 1 and 2 copies of instances of this
	original negative set were synthetically generated, respectively.
