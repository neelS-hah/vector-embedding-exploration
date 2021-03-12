| Table of Content | 
| -- |
| [1. Introduction](#1.-Introduction)|
| APA  | 91% | 0.91 |
| APBPA | 83% | 0.87 |

## 1. Introduction 
 
Are you using a Samsng, Huawei or Google phone? Are you aware that your phone is 50 times more likely to be hacked than an iphone which uses and IOS system? By July 2020, Android OS is still a leading mobile operating system that holds 74.6% of the market share worldwide, attracting numerous cyber-criminals who are targeting the largest crowd. Thus, developing a strong malware detection system becomes the number one priority.

<p float="center">
  <img src="Assets/images/android-malware.jpeg" width="100%" />
</p>

The current state of the art of Malware detection uses machine learning models built of static syntactic relationships between the codebase and corresponding API calls. 

## 2. Data Exploration
### Data Source

<p float="center">
  <img src="Assets/images/APK.png" width="100%" />
</p>

The applications from the Android Play Store are reduced to a version of assembly code for Java-based applications called Dalvik bytecode. The APK’s that contain the smali code are directly downloaded from ‘https://apkpure.com/’ and compiled into .smali files using the apktools library. Thus, this data is then unpackaged using the apktools library that allows us to view the subsequent smali code (a code that humans can interpret) and app binaries. The smali code and app binaries contain a lot of the information derived from the Java source code that allows us to map the number of API calls and the relationships between them. 

[Go to Data Exploration](./data.md)

## 3. Graph Embedding Techniques
Now that we’ve established base relationships across Apps and APIs through various adjacency matrices and baseline models. To better understand the relationships between API calls, and their subsequent properties we explore them through Graph Networks, their ability to learn and traverse, and the corresponding vectorized embeddings. 

### 3.1 Word2vec:

Word2Vec is one of the most popular techniques to learn word embeddings using a shallow neural network, developed by Tomas Mikolov in 2013 at Google.  Word2vec learns the association among words from a large corpus of text, and it could be used to find synonymous words or suggest an additional word for an incomplete sentence using Skip Gram or Common Bag Of Words (CBOW).

[Go to Word2Vec](./w2v.md)

### 3.2 Node2Vec:

Node2vec is an algorithmic framework for representational learning on graphs. Given any graph, it can learn continuous feature representations for the nodes, which can then be used for various downstream machine learning tasks.

Compared to the simple graph we have for Word2Vec, Node2vec can be applied to complexly structured graphs that are " (un)directed, (un)weighted, or (a)cyclic." To accomplish that, Node2vec generates biased random walks from each node of the graph. This provides a way of balancing the exploration-exploitation tradeoff by smoothly interpolating between BFS and DFS.

[Go to Node2Vec](./n2v.md)

### 3.3 Metapath2vec

Compared to Word2Vec and Node2Vec which use homogeneous graph networks, Metapath2Vec uses heterogeneous graph networks. Heterogeneous graph networks allow us to distinguish different types of nodes and edges(relationship). In our case, using heterogeneous graph networks enable us to see the difference between API and APP nodes. 

On the other hand, similar to Node2Vec, Metapath2Vec takes random walks to “construct the heterogeneous neighborhood of a node” and then uses “a heterogeneous skip-gram model to perform node embeddings.”

[Go to Metapath2Vec](./m2v.md)

## 4. Future Research
### Shortcomings 

1. Primarily with the given resources and ability to scale, we reached our ability of applications and APIs we could have used. Ideally compared to a lot of academic research and papers, we would want to scale our dataset by a factor of 30 times. 

### Future Research 

Primarily, in our project - we have 3 graph embedding techniques that are analyzed through their embeddings and models. These models could be expanded to be neural networks or architectures that better help predict embeddings than the current classification models.

There are multiple graph embedding models and techniques that go far beyond the ones explored today. Additionally, the scalability and ability to hyper optimize these embeddings their corresponding models exist to a large degree. 

Additionally, the research of adversarial models through the lens of Graph Embeddings allows a whole new aspect of risk and exploration. 


## 5. Conclusion

Overall, with a balance between feasibility of scaling and implementation, we found Node2vec most versatile, allowing us to retain accurate results while forming sentences and correlations that more closely represented the class division of applications.
It is often easy to forget while analyzing and writing code, that at the end of it all it’s still a language. Using technology and models designed for linguistic semantics and structure and using it on the binaries of a programming language and application is a meta-analysis that adequately serves its purpose. 

## 6.Additional Information

<a href="https://BorealBlizzard.github.io/page1.html/">Video Link to Our Presentation</a>


