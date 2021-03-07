## Introduction 
 
By July 2020, Android OS is still a leading mobile operating system that holds 74.6% of the market share worldwide, attracting numerous crazy cyber-criminals who are targeting the largest crowd.¹ Also, due to its open-resource feature and flexible system updating policy, it is 50 times more likely to get infected compared to ios systems.² Thus, developing a strong malware detection system becomes the number one priority.

Through the replication study of HinDroid from last quarter, we learned that HinDroid is an excellent technology for identifying malware. As other malware detection system simply use Application Programming Interface (API) calls, HinDroid further analyzes the relationship between API calls and higher-level semantics which raise the threshold for attackers.3 It is the first work to use Heterogeneous Information Network for Android Malware Detection.3

There are more technologies that could identify Malware. Thus, we decided to extend from what we’ve done for the replication and explore techniques to detect Android malware using Heterogeneous Graph. The techniques include Word2vec, Node2vec, and Metapath2vec. For a successful project, we are aiming to have an evaluation of each Graph Embedding Techniques and picking the best model.


## Overall Approach 
Topic 1 - Why our skillset is applicable for this project. Intended audience industry professionals.

Topic 2 - Define inspiration for merging discplines of core ML for malware detections as opposed to the idea of treating it more linguistically. 

## How Does One Even Access Malware Applications?
Topic 1 - This serves as our informal introduction to the project data. What it contains and how it also serves as training and testing data for further ML explorations

Topic 2 - A light explaination on procedure and what it took to pre-process the data

## A Story About Malware 
Topic 1 - Extracted findings from the EDA, trends of our dataset and other statistics that are derived from the dataset. 

This section will include plots and images to help understand the findings of our EDA, maybe a graph plot of all the api's and apps and their relations

Build the plot for the website to extend the understanding to current and state of the art for malware detection, what's currently used and what NLP techniques are proposed - Node2vec, MetaPath2Vec, Word2vec

Note - Will spend the most time explaining word2vec through examples and then using a related example for API's and Applications. 


## Our Results, Findings and Interesting Observations
Note - will provide hyperlinks and github repo references for technical aspects such as hyperparameters and model choice, although this section will speak through plotly graphs of how the two classes are divided through vetor embeddings and further analysis that's conducted through them. 

Will have a couple tables comparing success(or not) of ML model choices and techniques. Will also reference hindroid and how that project served to be the setting for everything that follows here (along with the hindroid results)



