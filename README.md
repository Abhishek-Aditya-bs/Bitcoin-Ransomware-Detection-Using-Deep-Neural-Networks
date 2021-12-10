# Bitcoin Ransomware Detection using deep neural networks

## Report Links
Literature Survey [Report](https://drive.google.com/file/d/11vb0aNbmLAiJf4WmARSgy5_DmnAvYWKn/view?usp=sharing)

Final Report [Report](https://github.com/iVishalr/Bitcoin-Ransomware-Detection/blob/main/Bitcoin-Ransomware-Detection.pdf)

## Crypto Ransomware

Sophisticated malware that prevents users from accessing their data using encryption techniques until a ransom is paid to the attacker. 
One of the most violent types - Entire department or company will come to a standstill even if just one machine is infected. 

Machine Learning algorithms have been proposed to detect the Ransomware Bitcoin addresses, but they do not generalise enough to classify addresses belonging to different malware families. 

## Objective

Neural networks capture the information granularity at various layers which helps to detect ransomware addresses in a more generalized way.

We propose a neural network model that performs slightly better compared to other models in metrics like Receiver Operating Characteristic (ROC), F1 score and accuracy.

## Dataset Description

Dataset from the UCI BitcoinHeistRansomwareAddressDataset Data Set available at [link](http://archive.ics.uci.edu/ml/datasets/BitcoinHeistRansomwareAddressDataset)

Number of instances: 2916697

Number of attributes: 10

Attribute Information

Features :

`address` : String. Bitcoin address.

`year` : Integer. Year.

`day` : Integer. Day of the year. 1 is the first day, 365 is the last day.

`length` : Integer.Length is designed to quantify mixing rounds on Bitcoin, where transactions receive and distribute similar amounts of coins in multiple rounds with newly created addresses to hide the coin origin.

`weight` : Float. Weight quantifies the merge behavior (i.e., the transaction has more input addresses than output addresses), where coins in multiple addresses are each passed through a succession of merging transactions and accumulated in a final address.

`count` : Integer. Similar to weight, the count feature is designed to quantify the merging pattern. However, the count feature represents information on the number of transactions, whereas the weight feature represents information on the amount (what percent of these transactions is output) of transactions.

`looped` : Integer. Loop is intended to count how many transaction i) split their coins; ii) move these coins in the network by using different paths and finally, and iii) merge them in a single address. 

`neighbors` : Integer. (Not explained in dataset, but assumed to be number of network neighbors involved in the transaction) 

`income` : Integer. Satoshi amount (1 bitcoin = 100 million satoshis).

`label` : Category String. Name of the ransomware family (e.g., Cryptxxx, cryptolocker etc) or white (i.e., not known to be ransomware).

## Implementation

Data preprocessing - 

Irrelevant features like year, day, Bitcoin address were dropped since they do not add any value to the classification. 
Log transformations were applied to convert highly right skewed features like the ones shown in the following image to normal distributions.

The features still have some skewness is left, but we can’t apply further more transformations, since values become nan or zero and reduce our training set size, and since we have implemented neural networks, they perform poorly with less data. So we decided to work with a single log transformation.

Model building -

The dataset was divided into 80% train and 20% test splits. Various scaling techniques like StandardScaler, MinMaxScaler, RobustScaler were applied to both the train and test data to scale them down appropriately.
Supervised classification machine learning models were applied like logistic regression, KNN, SVM, Decision Tree, Random Forest, AdaBoost, XGBoost, Neural Networks.

## Evaluation

As a part of evaluation we have used accuracy, recalll, precision, f1 score and roc score metrics to compare amongst the models.

For comparison of the model performance we used ROC metric and plotted the ROC Graph. Here u can see all the models are better than a random classifier, and neural netwroks have a sligh better score than other algorithms. This score can be imporved if we had more balanced data, since neural netwroks outperform other models when more training data is available.





