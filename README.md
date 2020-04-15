# PPI-RCC
Supplementary material for the publication entitled "Protein-Protein interactions efficiently modeled by residue cluster classes" by Albros Hermes Poot Velez, Fernando Fontove and Gabriel Del Rio

This repositry contains 7 directories:

	i) testing_sets: The 24 testing sets used for this work in arff format.

The following folders contain the algorithms resulting of the training sets, compressed with XZ Utils:

	ii) training_models_compressed_norm_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset normilized and a distance criterion of 7 Å.

	iii) training_models_compressed_norm_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset normilized and a distance criterion of 8 Å.

	iv) training_models_compressed_raw_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset raw and a distance criterion of 7 Å.

	v) training_models_compressed_raw_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset raw and a distance criterion of 8 Å.

	vi) training_models_compressed_stand_7: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset standardized and a distance criterion of 7 Å.

	vii) training_models_compressed_stand_8: 60 algorithms resulting of AutoWEKA Bayesian search on the training set with the dataset standardized and a distance criterion of 8 Å.


After decompressing the training_models, to test this algorithms is needed to identify its corresponding testing_set. For this mean, the first 3 fields on each file (separated by underscore), are the same between testing (i) and training files (ii-vii). 

The following is an example of the the code to test the algorithms:

	java -Xmx{MEML}m -cp {AUTOWEKA} {CLASS} -T {TES} -l {MOD} > {OUT}

In which the terms between braces are replaced as follow (whitout the braces):

	MEML = The limit memory to use for executing the java virtual machine
	AUTOWEKA = /The/path/to/Auto-WEKA/autoweka.jar file 
	CLASS = The WEKA class: 'weka.classifiers.meta.AutoWEKAClassifier'
	TES = The testing_set_file.arff
	MOD = The corresponding training_model_file.mod 
	OUT = Optional. The file in which the output will be redirected, otherwise it will be sent to the standard output




Abbreviations:

	norm = normalization used in the construction of the training or testing data sets
	stand = standardized used in the construction of the training or testing data sets
	raw = data used as is in the training or testing set
	7 = distance of 7 Å used to generate the contact map
	8 = distance of 8 Å used to generate the contact map
	noSC = without side chain
	yesSC = with side chain
	con = concatenation of RCC
	sum = sum of RCC
	under = the type of undersampling used
	PPI = Protein-Protein interaction.
	P = positive PPI pairs of proteins
	N = negative PPI pairs of proteins
	sz1 = undersampling 1:1 (P:N)
	sz2 = undersampling 2:1 (P:N)
	sz3 = undersampling 3:1 (P:N)
	it1, it2 or it3 = the random iteration seed used for the undersampling
	over200 = the synthetic oversampling used to generate the same quantity of negative instances 1:2 (P:N)
	over300 = the synthetic oversampling used to generate twice the quantity of negative instances 1:3 (P:N)

