## Introduction 
 
By July 2020, Android OS is still a leading mobile operating system that holds 74.6% of the market share worldwide, attracting numerous crazy cyber-criminals who are targeting the largest crowd.¹ Also, due to its open-resource feature and flexible system updating policy, it is 50 times more likely to get infected compared to ios systems.² Thus, developing a strong malware detection system becomes the number one priority.

Through the replication study of HinDroid from last quarter, we learned that HinDroid is an excellent technology for identifying malware. As other malware detection system simply use Application Programming Interface (API) calls, HinDroid further analyzes the relationship between API calls and higher-level semantics which raise the threshold for attackers.3 It is the first work to use Heterogeneous Information Network for Android Malware Detection.3

There are more technologies that could identify Malware. Thus, we decided to extend from what we’ve done for the replication and explore techniques to detect Android malware using Heterogeneous Graph. The techniques include Word2vec, Node2vec, and Metapath2vec. For a successful project, we are aiming to have an evaluation of each Graph Embedding Techniques and picking the best model.


## Data Exploration
### Data Collection
The data(source code) for identifying malware is primarily the android play store, although in order to obtain the respective APK’s for these apps the data is directly downloaded from ‘https://apkpure.com/’. Nonetheless, the code that directly downloaded cannot be interpreted by us directly.

Thus, this data is then unpackaged using the apktools library that allows us to view the subsequent smali code (a code that humans can interpret) and app binaries. The smali code and app binaries contain a lot of the information derived from the Java source code that allows us to map the number of API calls and the relationships between them. 

We extracted the datasets of the source code of each app from our section resource, which includes a total of 300 apps. The benign apps are picked randomly. For the malware apps, we specifically picked malware apps that are type Anup and RuMMS. More datasets and EDA of the datasets will be included in the future to achieve a more accurate and convincing result. 
### Data Processing and Cleaning 
Each app has multiple files and folders, offering a large amount of code to be processed. We walked through each .smali file to collect the features we need.

1. We select API calls and dissect them into different parts: API itself, code block, and package. 
(pic)
2. Then, we use these parts to create matrices of A, B, and P.
(pic)
3. Based on the matrices, we explored meta path AA^T, ABA^T, APA^T, and APBP^TA^T, and used multi-kernel learning to compute the similarities.
(pic)

Topic 2 - Define inspiration for merging discplines of core ML for malware detections as opposed to the idea of treating it more linguistically. 

## Vector Embedding Analysis and Exploration
To visualize the Embedding Techniques, 
1. we imported gensim.models.keyedvectors to vectorize the apps
2. Then we visualize the high-dimension vector using scipy.TSNE, which allowed us to reduce the dimension of the vector embeddings to 2. So, we can visualize the vectors in a 2-D graph.
3. (For further work, we are going to explore if we can successfully classify benign apps and malware apps from the embedding vectors using SVM models.)

### Word2vec:
（pic)

## A Story About Malware 
Topic 1 - Extracted findings from the EDA, trends of our dataset and other statistics that are derived from the dataset. 

This section will include plots and images to help understand the findings of our EDA, maybe a graph plot of all the api's and apps and their relations

Build the plot for the website to extend the understanding to current and state of the art for malware detection, what's currently used and what NLP techniques are proposed - Node2vec, MetaPath2Vec, Word2vec

Note - Will spend the most time explaining word2vec through examples and then using a related example for API's and Applications. 


## Our Results, Findings and Interesting Observations
Note - will provide hyperlinks and github repo references for technical aspects such as hyperparameters and model choice, although this section will speak through plotly graphs of how the two classes are divided through vetor embeddings and further analysis that's conducted through them. 

Will have a couple tables comparing success(or not) of ML model choices and techniques. Will also reference hindroid and how that project served to be the setting for everything that follows here (along with the hindroid results)



