# Citation-needed-paper
Repository of data and code to use the models described in the paper "Citation Needed: A Taxonomy and Algorithmic Assessment of Wikipedia's Verifiability"

### Detecting Citation Need
The repository provides data and models to score sentences according to their "citation need", i.e. whether an inline citation is needed to support the information in the sentence. Models are implemented in Keras.

#### Using Citation Need Models
The *test_citation_need_model.py* script takes as input a text file containing statements to be classified, and gives as ouput a "citation need" score of reach sentence.

To run the script, you can use the following command:
```
python test_citation_need_model.py -i input_file.txt  -m models/model.h5 -v dicts/word_dict.pck -s dicts/section_dict.pck -o output_folder -l it
```

Where:
- **'-i', '--input'**, is the input .csv file from which we read the statements. Tab-separated columns should contain at least the following tab-separated values (and the corresponding header): 
  - "statement", i.e. the text of the sentence to be classified
  - "section", i.e. the section title where the sentence is located
  - "citation", the binary label corresponding to whether the sentence has a citation or not in the original text. This can be set to 0 if no evaluation is needed. 
An example input file is provided in *test_input_data_sample.txt*

- **'-o', '--out_dir'**, is the output directory where we store the results
- **'-m', '--model'**, is the path to the model which we use for classifying the statements.
- **'-v', '--vocab'**, is the path to the vocabulary of words we use to represent the statements.
- **'-s', '--sections'**, is the path to the vocabulary of section with which we trained our model.
- **'-l', '--lang'**, is the language that we are parsing now, e.g. "en", or "it".



#### Models and Data
The _models_ folder contains the links to the citation need models for _English_, _French_, and _Italian_ Wikipedias, trained on a large corpus of Wikipedia's Featured Articles. The training data for these articles, as well as more training data for other models described in the paper can be found in the _training_data_ folder.


### System Requirements
There are some requirements for this script to run smoothly. Below are the versions which they’d need to have in order to run this script.  

Python 2.7 
Keras 2.1.5
Tensorflow 1.7.0
sklearn 0.18.1

### Citing this work
When using this dataset, please use the following citation:

```
@inproceedings{Redi:2019:CNT:3308558.3313618,
 author = {Redi, Miriam and Fetahu, Besnik and Morgan, Jonathan and Taraborelli, Dario},
 title = {Citation Needed: A Taxonomy and Algorithmic Assessment of Wikipedia's Verifiability},
 booktitle = {The World Wide Web Conference},
 series = {WWW '19},
 year = {2019},
 isbn = {978-1-4503-6674-8},
 location = {San Francisco, CA, USA},
 pages = {1567--1578},
 numpages = {12},
 url = {http://doi.acm.org/10.1145/3308558.3313618},
 doi = {10.1145/3308558.3313618},
 acmid = {3313618},
 publisher = {ACM},
 address = {New York, NY, USA},
 keywords = {Citations, Crowdsourcing, Neural Networks;, Wikipedia},
} 
```

