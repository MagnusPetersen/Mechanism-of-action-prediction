# Mechanism-of-action-prediction
My Kaggle challenge notebooks for the "Mechanism of Action" contest. All my iterations and insights. This was my first Kaggle challenge, as such it is not fully optimized, as I wanted to get a feel for the competions first.

# Challenge Outline

The goal of the challenge is to use 100 cell viability features and 772 gene expression features to find the corrsponding 206 target mechanisms. The features are the results from the L1000 and Prism assay respectively. The problem is therefore a simple classification problem where the complexity comes from the amount of categories and their imbalance. 

# Approaches
Baseline: My baseline model was a fully connected neural network with only the necessary data rescaling. As expected the results were not that great with a logit loss of 0.019.

TabNet: As the next model to improve upon the base line TabNet and XgBoost were picked, since they both deal well with tabular data. XgBoost performed barely better than the baseline and therefore TabNet was choosen for the continued refinement of the solution. 

TabNet [1] is an attention based network, that sequentially resions over features to reach a decision. The power of attention based methods has been not only powerfull but in this vase also leads to further interpretability. Just using TabNet a result of 0.0174 was archieved. 

TabNet with feature engineering: Using Kernel PCA on the data 100 principle components were calculated to bolster the data, this improved accuracy by an insignifant amount. Furthermore I trained an Autoencoder with 40 latents to encode the data and add the encoded version to the data feed into the TabNet. This imporved the performance to 0.0165. 

The perfomance on the hidden Kaggle test set is noticably worse than on the validation set. This appears to be due to the large amount of lables and the rarity of a few of those. An 80/20 train-validation split is suboptimal in thi situation, as it migth stop the model from seeing some of the rarer lables more frequently. A Kflod split migth be better in this case. 

Using K-Fold split the performance stayed the same on the different validation sets but improved on the hidden set by.... 

# Insigths

Using the attention masks of the TabNet you can glimpse certain insigths from the decission making process. 









[1] TabNet: Attentive Interpretable Tabular Learning, Sercan O. Arik, Tomas Pfister https://arxiv.org/abs/1908.07442
