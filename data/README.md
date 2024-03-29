# ADS Project 1: Understanding Happy Moments
### Data folder

The data directory contains data used in the analysis. Original data imported from [HappyDB](https://rit-public.github.io/HappyDB/). HappyDB is a corpus of 100,000+ crowd-sourced happy moments. The goal of the corpus is to advance the state of the art of understanding the causes of happiness that can be gleaned from text.

### Directory Structure
After you clone or download the repository, you will see the following file structure.
```
   data
    ├── cleaned_hm.csv
    ├── demographic.csv
    ├── original_hm.csv
    ├── senselabel.csv
    ├── topic_dict
    │   ├── entertainment-dict.csv
    │   ├── exercise-dict.csv
    │   ├── family-dict.csv
    │   ├── food-dict.csv
    │   ├── people-dict.csv
    │   ├── pets-dict.csv
    │   ├── school-dict.csv
    │   ├── shopping-dict.csv
    │   └── work-dict.csv
    └── vad.csv
```
HappyDB consists of a set of CSV files. Here are schema descriptions of the files.

#### ```cleaned_hm.csv```
cleaned_hm.csv contains cleaned-up happy moments and some additional information in addition to original happy moments.

- hmid (int): Happy moment ID
- wid (int): Worker ID
- reflection_period (str): Reflection period used in the instructions provided to the worker (3m or 24h)
- original_hm (str): Original happy moment
- cleaned_hm (str): Cleaned happy moment
- modified (bool): If True, original_hm is "cleaned up" to generate cleaned_hm (True or False)
- predicted_category (str): Happiness category label predicted by our classifier (7 categories. Please see the reference for details)
- ground_truth_category (str): Ground truth category label. The value is NaN if the ground truth label is missing for the happy moment
- num_sentence (int): Number of sentences in the happy moment

#### ```original_hm.csv```
original_hm.csv contains unfiltered version of happy moments.

- hmid (int): Happy moment ID
- wid (int): Worker ID
- hm (str): Original happy moment
- reflection_period (str): Reflection period used in the instructions provided to the worker (3m or 24h)

#### ```demographic.csv```
demographic.csv contains demographic information of the workers who contributed to the happy moment collection.

- wid (int): Worker ID
- age (float): Age
- country (str): Country of residence (follows the ISO 3166 Country Code)
- gender (str): {Male (m), Female (f), Other (o)}
- marital (str): Marital status {single, married, divorced, separated, or widowed}
- parenthood (str): Parenthood status {yes (y) or no (n)}

#### ```senselabel.csv```
senselabel.csv contains multi-word expression and supsersense tags on "cleaned" happy moments. Thus, the number of rows are exactly same as that of cleaned_hm.csv.

- hmid (int): Happy moment ID
- tokenOffset (int): Position index of a token
- word (str): Token in the original form
- lowercaseLemma (str): Lemmatized token in lowercase
- POS (str): Part-of-Speech tag
- MWE (str): Multi-word expression (MWE) tag in the extended IOB style (See [REF] for further information)
- offsetParent (int): The beginning position of a multi-word expression
- supersenseLabel (str): Supersense classes defined in the WordNet (19 verb and 25 noun classes. See [REF] for further information.)

### References
Akari Asai, Sara Evensen, Behzad Golshan, Alon Halevy, Vivian Li, Andrei Lopatenko, 
Daniela Stepanov, Yoshihiko Suhara, Wang-Chiew Tan, Yinzhan Xu, 
``HappyDB: A Corpus of 100,000 Crowdsourced Happy Moments'', LREC '18, May 2018.
