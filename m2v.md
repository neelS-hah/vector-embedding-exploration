### 3.3 Metapath2vec
#### Introduction - 

Compared to Word2Vec and Node2Vec which use homogeneous graph networks, Metapath2Vec uses heterogeneous graph networks. Heterogeneous graph networks allow us to distinguish different types of nodes and edges(relationship). In our case, using heterogeneous graph networks enable us to see the difference between API and APP nodes. 

On the other hand, similar to Node2Vec, Metapath2Vec takes random walks to “construct the heterogeneous neighborhood of a node” and then uses “a heterogeneous skip-gram model to perform node embeddings.”

#### Implementation - 

We leveraged decisions based on the analysis from previous models for metapath2vec, allowing us to focus on scalability and the versatility of the model.
Metapath2Vec unlike the previous models through heterogeneous walks is able to capture less biased data through chaining together multiple API’s. For the purpose of this research we focus on the native Metapath2Vec implementation and not it’s Metapath2Vec ++ implementation which adds negative sampling functionality.

For metapath2vec the implementation involved selecting a random application and finding a corresponding uniformly probable API that has been found in the application. Once this is found, we extract a corresponding API from the from the column where it is found in other applications. This process of moving through the matrices with App → API relationships allows us to create meta paths. 


#### Analysis - 
| Meta-Path Walks | Accuracy | F1 Score |
| -- | -- | -- |
| APA  | 94% | 0.95 |
| APA  | 91% | 0.91 |
| APBPA | 83% | 0.87 |
