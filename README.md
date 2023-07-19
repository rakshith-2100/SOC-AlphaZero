# SOC-AlphaZero
## DataSet
Used the data from a CCRL website (www.computerchess.org.uk/ccrl) converted it into bitstrings considering 10 random positions from each game and then used  these  bitstrings for training
## Model
The Model is devided into two parts one is the pos2vec model and siamese model.
### Stacked Autoencoders model(Pos2Vec)
The Pos2Vec Model which is a 5 layer network i.e 773-600-400-200-100 where the trained weights were used as initial weights. Initially trained 1st layer(i.e , a 773-600-773 autoencoder and then of 600-400-600 autoencoder andd so on...this was trained for 200 epochs.
### Siamese Network
This is a supervized training phase where two copies of pos2vec were added and then added 4 layers i.e ,400-200-100-2 .1st 5 layers were feature extractors and last 4 were to compare which feature is better. We train this network with 1000 epochs and the weights get updated 
## Training Phase 
Achieved a training accuracy of 100% with 0 training loss after 1000 epochs and tested the model and then achived the accuracy of 88% which is decent number but sure there was a significant decrease in the accuracy.
