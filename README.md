# Mechanism-of-action-prediction
My Kaggle challenge notebooks for the "Mechanism of Action" contest. All my iterations and insights. This was my first Kaggle challenge, as such it is not fully optimized, as I wanted to get a feel for the competions first.

# Challenge Outline

The goal of the challenge is to use 100 cell viability features and 772 gene expression features to find the corrsponding 206 target mechanisms. The features are the results from the L1000 and Prism assay respectively. The problem is therefore a simple classification problem where the complexity comes from the amount of categories and their imbalance. 

# Approaches
Baseline: My baseline model was a fully connected neural network with only the necessary data rescaling. As expected the results were not that great with a logit loss of 0.019.

TabNet: As the next model to improve upon the base line TabNet and XgBoost were picked, since they both deal well with tabular data. XgBoost performed barely better than the baseline and therefore TabNet was choosen for the continued refinement of the solution. 

TabNet is an attention based network, that sequentially resions over features to reach a decision. The power of attention based methods has been not only powerfull but in this vase also leads to further interpretability. 
