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

#### Word2vec:
（pic)
#### Node2Vec:
(pic)
(pic)
## Graph Embedding Techniques
### Word2Vec
Word2Vec is one of the most popular techniques to learn word embeddings using a shallow neural network, developed by Tomas Mikolov in 2013 at Google.  Word2vec learns the association among words from a large corpus of text, and it could be used to find synonymous words or suggest an additional word for an incomplete sentence using Skip Gram or Common Bag Of Words (CBOW).

For this particular analysis, we constructed a graph traversal for the word to vector embeddings using the APA relationship. An APA relationship is a meta-path: App→(contains)API→(same package name)API→(contains-1)APP. In this relationship, we are not only calculating the similarity of APIs between 2 APPs, but also calculating if the APIs are from the same package. After this, we can then use the dot product to calculate the similarity.

It’s is connecting an application and api in addition to the api calls that occur in similar packages and their corresponding applications. This allows us to pierce through the relationships of malware and benign applications. 

This relationship is expressed as embeddings which we then visualize on the 2-Dimensional plane to further use clustering techniques to classify the application types. 


### Node2Vec
Node2vec is an algorithmic framework for representational learning on graphs. Given any graph, it can learn continuous feature representations for the nodes, which can then be used for various downstream machine learning tasks.

Compared to the simple graph we have for Word2Vec, Node2vec can be applied to complexly structured graphs that are " (un)directed, (un)weighted, or (a)cyclic." In order to accomplish that, Node2vec generates biased random walks from each node of the graph. This provides a way of balancing the exploration-exploitation tradeoff by smoothly interpolate between BFS and DFS.

Using random walks through the corpus, we created multiple documents as an input into the Gensim model for vectorizing embeddings using sentences. These embeddings were then analyzed using their corresponding graph clusters. 
The purpose of random walks are to add context to the Application → API nodes, by looking at corresponding applications or API’s that are neighbors to the starting applications. 

In the figure under node2vec above we clearly see the distinction between the two classes. On visualizing this on a 2-Dimensional plane it is now possible to use lighter classification models to help classify benign vs malware applications.

### Metapath2Vec
Comparing to Word2Vec and Node2Vec which use homogeneous graph networks, Metapath2Vec uses heterogeneous graph networks. Heterogeneous graph networks allow us to distinguish different types of nodes and edges(relationship). In our case, using heterogeneous graph networks enable us to see the difference between API and APP nodes. 

On the other hand, similar to Node2Vec, Metapath2Vec takes random walks to “construct the heterogeneous neighborhood of a node” and then uses “a heterogeneous skip-gram model to perform node embeddings.”6 

## Conclusion



