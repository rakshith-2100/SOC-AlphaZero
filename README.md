# SOC-Deep-Carlsen
In the project I would create a AI-Chess model that would make a comparision between the the states, determining the best winning state from the set of states in a chess game.In this project I have taken dataset from a CCRL website which has a data of 640000 chess games.
## Data Processing
The Dataset was taken from the CCRL website (www.computerchess.org.uk/ccrl). In which 10 random positions(Win or loos) where taken from each game and these postions were converted to bitstrings and these  bitstrings were used for the training process. In the Code, out of 640000 games 20000 games were taken into account and 110670 winning and 87269 loosing positions were obtained in which around 80000 W/L positions were considered.
## Model
In the project I have used to models pos2vec model and siamese model. I have explained about the model below.
### Stacked Autoencoders model(Pos2Vec)
In the Pos2Vec model we train stacked autoencoders, which would serve as the weights for the supervized training.This network contains 5 connected layers i.e, 773-600-400-200-100. We Trained the 1st layer by a 3-layer autoencoder(773-600-773) and trained 5-layer autoencoder(773-600-400-600-773) and so on. The datset used here is a set of 40000 W/L positions and trained with 200 epochs. in this training No regularization is used.
### Siamese Network
This is the core component of our method. Here we used the weights of Pos2Vec DBN as the initial weights for the supervized networks. We take 2 copies of Pos2Vec side by side  and then 4 connected layers 400-200-100-2 are added to the Pos2Vec model. The first 5 layers severe as a high feature extractors as the wieghts were obatined from unsupervized learning technique and then these features get compared in the last 4 layers of the network Thus determining the best position in the game.
## Training Phase 
We trained the network using 100 epochs. In each epoch two random states were taken into the cosideration and were compared. The pairs were randomly orederd either (W,L) or (L,W). I didnot use any regularzation term. The activation used in each layer is ReLU. The learning rate here was 0.01 and Cross Entophy Loss was used. Trained this model and then achieved a training accuracy of 100% with 0 training loss after 1000 epochs and tested the model and then achived the a test accuracy of 88% which is a  decent number but sure there was a significant decrease in the accuracy which means it has a high variance which can be reduced by some regularization techniques.
## References Used
1) https://www.cs.tau.ac.il/~wolf/papers/deepchess.pdf
2) https://github.com/navyanshmahla/deep-carlsen-SoC23/blob/main/Reading%20Material.md
3) https://www.youtube.com/watch?v=P0jd8AHwjXw&list=WL&index=13&t=2566s
