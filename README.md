# Facebook Network Analysis

## Outline
The goal is to solve a link prediction task on ego-net facebook data. This can have applications in, for instance, finding suspects in a police investigation based on the ego-nets constructed of the interrogated criminals. 

This is done by firstly importing the data and merging the ego-nets into one large network. This is done in the `preprocessing` notebook. Subsequently, the resulting network can be displayed by running the `display_network` notebook and opening the resulting `facebook_network.html`. Some network properties can be observed by running the `graph_statistics` notebook.

To start a link prediction task, it is essential to create a node embedding. For this research two different node embeddings are tested: Node2Vec (single node representation) and Splitter (multiple node representation). Then, the embeddings can be used as input to downstream machine learning algorithms. In this research, we use ....

## Preprocessing

1. Make sure to have the data available [here](https://snap.stanford.edu/data/ego-Facebook.html) downloaded and saved in a folder `/data/`. This folder is ignored by git.
2. Run `preprocessing.ipynb` to convert the data from `/data/facebook_combined.txt` and `/data/facebook/` into workable network files.

## Node Embeddings
### Node2Vec

1. Run `pip install node2vec` in your prefered environment
2. Then you can run the `node2vec` notebook to generate a single node representation embedding in `embedded_data/node2vec.txt`

### Splitter

1. .....

## Link Prediction

1. .....

## Citations:
Aditya Grover and Jure Leskovec. “Node2vec: Scalable Feature Learning for Networks”, 2016. Doi: 1607.00653

Alessandro Epasto and Bryan Perozzi. “Is a Single Embedding Enough? Learning Node Rep-resentations that Capture Multiple Social Contexts”. In: The World Wide Web Conference, ACM, May 2019. Doi: 10.1145/3308558.3313660