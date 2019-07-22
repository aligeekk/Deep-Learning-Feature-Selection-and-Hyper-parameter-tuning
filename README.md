1.	Dataset

This project uses a Network Intrusion Detection dataset called IDS 2017 captured by Iman Sharafaldin, Arash Habibi Lashkari, and Ali A. Ghorbani at the University of New Brunswick [1]. The dataset originally had around 2.8 million samples and 77 features which I cleaned and under-sampled to 494427 samples as part of another project. The labels in the dataset has 9 classes which include normal behavior as 0 and, 8 attacks Brute Force FTP, Brute Force SSH, DoS, Heartbleed, Web Attack, Infiltration, Botnet and DDoS as integers 1 to 8.

2.	Approach

Feature selection: ExtraTreeClassifier is used to rank the features of the dataset and only 16 most important features are used to train and evaluate all the models. 
Dataset split: The dataset after feature selection is split into 3 parts; training set, cross-validation set and test set. 50% of the dataset is used for training purpose while cross-validation set and test set both consist of 25% of the dataset. 

1-layer neural network: 1-layer neural network is trained using training set and evaluated using the test set without hyper-parameter tuning. It consists 1-hidden layer with 9 hidden units and uses softmax as an activation function while adam is used as optimizer. The number of epochs and batch size are 10 and 128 respectively. All the other parameters use default values.
4-layer neural network: 4-layer neural network is trained using training set and evaluated using the test set without hyper-parameter tuning. It consists of 4 hidden layers which have 9, 8, 6 and 9 hidden units respectively. First 3 layers use relu as activation function while the output layer use softmax activation function. The optimizer used is adam. The number of epochs and batch size are 10 and 128 respectively. All the other parameters use default values.
Convolutional Network without hyper-parameter tuning: Then, convolutional network is trained and evaluated using training and test datasets respectively, again without hyperparameter tuning. All the layers except the final layer use relu as activation function while output uses softmax. The optimizer used is adam. The number of epochs and batch size are 10 and 128 respectively. All the other parameters use default values.
Convolutional Network with hyper-parameter tuning: In the final model, hyper-parameters such as number of epochs, number of batches, optimizer and learning rate for optimizer are tuned using KerasClassifier and GridSearchCV modules of the scikit-learn package. All the layers except the final layer use relu as activation function while output layer uses softmax. The optimizer used is adamax. The number of epochs and batch size are 100 and 32 respectively. The learning rate for adamax optimizer is 0.01. The values for epochs, batch size, optimizer and learning rate are the results of hyper-parameter tuning. 

References
1.	I. Sharafaldin, A.H. Lashkari, and A. A. Ghorbani, Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization, 4th International Conference on Information Systems Security and Privacy (ICISSP) (2018)
