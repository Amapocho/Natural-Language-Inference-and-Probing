# Natural Language Inference and Probing

## Natural Language Inference on SNLI Dataset

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

![Validation Accuracy vs Number of BiLSTM layers](https://github.com/Amapocho/Natural-Language-Inference-and-Probing/blob/main/Graphs/Validation%20Accuracy%20vs%20Number%20of%20BiLSTM%20layers.png)

The model only had to be trained for 15 epochs after which it started to overfit/plateau.

![Training and Validation Loss](https://github.com/Amapocho/Natural-Language-Inference-and-Probing/blob/main/Graphs/Loss.png)

![Training and Validation Accuracy](https://github.com/Amapocho/Natural-Language-Inference-and-Probing/blob/main/Graphs/Accuracy.png)

## Probe

I constructed a POS probe to analyse the model. It took the output from the different internal layers of
the inference model, passed it through a dense neural net to predict the POS tag of the words given as
input.

To extract the POS tags from the dataset I iterated over the sentences given in the parsed tree format. I
tokenized both the words and the tags before passing it through the aforementioned model.

I carried out probing on 3 different models I had tried while training for inference so as to analyse the
difference and understand how the model calculates and interprets English language
