# Fake-news-detection-by-using-deep-learning-
Data preprocessing 
1)	Perform various text cleaning steps (remove all non-alphanumeric characters ,delete stopwords, delete missing rows etc.)
2)	For DOC2VEC ,convert to labeled sentences ,comma separated word format

Training Model used
1)	Neural Network
2)	Long Short Term Memory (LSTM)

Comparison of model
1) Nueral network using keras - 92.15% Accuracy
2)LSTM - 94.31% Accuracy

Implementation of paper on fake news detection 
Published by 
John Curci
College of Engineering
Boston University
Boston, MA 02215
jcurci92@bu.edu

Feed-forward Neural Network
I  implemented  feed-forward neural network model, using using Keras. Neural networks are commonly used in modern NLP applications  in contrast to older approaches which primarily focused on linear models such as SVM’s and logistic regression. My neural network implementation use three hidden layers. In  the Keras implementation I used layers of size 256, 256, and 80, interspersed with dropout layers to avoid overfitting. For activation function, i chose the Rectified Linear Unit (ReLU), which has been found to perform well in NLP applications.

Long Short-Term Memory
The Long-Short Term Memory (LSTM) is good at classifying serialized objects because it will selectively memorize the previous input and use that, together with the current input, to make prediction. The news content (text) in the problem is inherently serialized. The order of the words carries the important information of the sentence.So the LSTM model suits for the problem.Since the order of the words is important for the LSTM unit, I cannot use the Doc2Vec for preprocessing because it will transfer the entire document into one vector and lose the order information.To prevent that, i use the word embedding instead. I first clean the text data by removing all characters which are not letters nor numbers. Then I
count the frequency of each word appeared in  training dataset to find 5000 most common words
and give each one an unique integer ID. For example, the most common word will have ID 0, and
the second most common one will have 1, etc. After that replace each common word with its
assigned ID and delete all uncommon words. Notice that the 5000 most common words cover the
most of the text,  so only lose little information but transfer the string to a list of integers. Since the LSTM unit requires a fixed input vector length, truncate the list longer than 500 numbers because more than half of the news is longer than 500 words . Then for those list shorter than 500 words,  pad 0’s at the beginning of the list.also delete the data with only a few words since they don’t carry enough information for training. By doing this,  transfer the original text string to a fixed length integer vector while preserving the words order information. Finally  use word embedding to transfer each word ID to a 32-dimension
vector. The word embedding will train each word vector based on word similarity. If two words
frequently appear together in the text, they are thought to be more similar and the distance of their
corresponding vectors is small. The pre-processing transfers each news in raw text into a fixed size matrix. Then  feed the processed training data into the LSTM unit to train the model. The LSTM is still a neural network.But different from the fully connected neural network, it has cycle in the neuron connections. So the previous state (or memory) of the LSTM unit ct will play a role in new prediction.



