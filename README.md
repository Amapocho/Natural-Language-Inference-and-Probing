# Natural Language Inference and Probing

##  Dataset

I decided to go with a model with an embedding layer followed by a linear translation layer and
then two layers of bi-directional LSTM. After passing the premise and hypothesis through these
layers, they were concatenated and then passed through 5 dense layers with dropout.

In the model I chose, using Bidirectional LSTMs are very important. In the chosen number of
epochs (15) a model with Non- Bidirectional LSTMs showed no learning with accuracy
stagnating in and around 33%


|        | Validation Accuracy |
|--------|---------------------|
| BiLSTM | 79.60               |
| LSTM   | ~33%                |

I tried using various number of layers for BiLSTM, and found that accuracy peaked at a 2 layered model.

![Validation Accuracy vs Number of BiLSTM layers](/Graphs/Validation Accuracy vs Number of BiLSTM layers.png)
