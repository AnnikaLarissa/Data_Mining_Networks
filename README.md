# Facebook Network Analysis

## Outline
The goal is to solve a link prediction task on ego-net facebook data. This can have applications in, for instance, finding suspects in a police investigation based on the ego-nets constructed of the interrogated criminals. 

This is done by firstly importing the data and merging the ego-nets into one large network. This is done in the `preprocessing` notebook. Subsequently, the resulting network can be displayed by running the `display_network` notebook and opening the resulting `facebook_network.html`. Some network properties can be observed by running the `graph_statistics` notebook.

To start a link prediction task, it is essential to create a node embedding. For this research two different node embeddings are tested: Node2Vec (single node representation) and Splitter (multiple node representation) with different dimensions. Then, these embeddings can be used as input to downstream machine learning algorithms. In this research, we use logistic regressing and cosine similarity.

## Preprocessing

1. Make sure to have the data available [here](https://snap.stanford.edu/data/ego-Facebook.html) downloaded and saved in a folder `/data/`. This folder is ignored by git.
2. Run `preprocessing.ipynb` to convert the data from `/data/facebook_combined.txt` and `/data/facebook/` into workable network files.

## Node Embeddings
### Node2Vec

1. Run `pip install node2vec` in your prefered environment
2. Then you can run the `node2vec` notebook to generate single node representation embeddings in `/embedded_partial_data/`. For instance `/embedded_partial_data/node2vec_64.csv` is the 64 dimensional node2vec embedding on the graph with removed links.

### Splitter

1. The Splitter implementation uses PyTorch in a similar manner as https://github.com/benedekrozemberczki/Splitter. Make sure to have the required packages (and versions) installed before running the code.
2. Put the input data in `node_embeddings\splitter\input`
3. Potentially change the number of dimensions of the embedding, or other parameters such as number of walks in `node_embeddings\splitter\param_parser.py`
4. Run `python main.py` in your terminal. The embeddings appear in `node_embeddings\splitter\output`

## Link Prediction
### Logistic Regression

The `link_prediction_log_regression` takes the partial embeddings in `embeddings_parial_data` and `\splitter\output`. It splits the data into train (80%) and test (20%) sets and calculates the probability of the existence of an edge between nodes. This is then used to calculate the AUC-ROC, AUC-PR, accuracy and F1 score.

### Cosine Similarity
The `link_prediction_cosine_sim` notebook takes the partial embeddings in the `embeddings_parial_data` folder and iteratively predicts links if the cosine similarity >= 97.5%. Then, it compares it to the ground truth and outputs the confusion matrix, accuracy and precision for each of the dimensions.

## Citations:
Aditya Grover and Jure Leskovec. “Node2vec: Scalable Feature Learning for Networks”, 2016. Doi: 1607.00653

Alessandro Epasto and Bryan Perozzi. “Is a Single Embedding Enough? Learning Node Rep-resentations that Capture Multiple Social Contexts”. In: The World Wide Web Conference, ACM, May 2019. Doi: 10.1145/3308558.3313660