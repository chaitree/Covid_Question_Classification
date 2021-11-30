# Covid_Question_Classification
## Required libraries: 
Environment – python3 and jupyter-lab
1.	Pandas
2.	Matplotlib
3.	Seaborn
4.	nltk
5.	sklearn 
6.	wordcloud 
7.	random 
8.	yaml
9.	nlpAUG
10.	gensim 
11.	numpy 
12.	os

## How to execute the scripts:  <br />
### EDA and dataset split into train test  <br />
1.	Create data_generated folder in working directory where all scripts are there and train, test and author generated test data will be kept. “final_master_dataset.csv” must be in the same folder. <br />
2.	 Change values of parameters in data_config.yaml file <br />
a.	author_data_choice : (bool) to consider author generated test data for testing or not <br />
b.	test_percent : (int) percentage of test data during train test split of the data (coming from all sources except author)  <br /> 
c.	data_augmentation : (bool) to consider augmented train data for training or not  <br />
3.	Run EDA.ipynb to get and visualize different insights on data and generate train, test, author test data split of the dataset.  <br />
Files gets generated in data_generated folder : train dataset, test dataset and test data generated by author  <br />
### Data Augmentation  <br />
4.	If data augmentation in needed, run Data_Augmentation.ipynb file. In this case, we need to keep data_augmentation to be True in data_config.yaml  <br />
### Classification using tf-idf  <br />
We are using two classifiers , SVM (Support Vector Machine) classifier and MLP (Multilayer perceptron or simple neural network with n hidden layers) <br />
5.	Change values of parameters in SVM_classifier_config.yaml file <br />
a.	kernel_name_SVM : kernel used to build SVM like linear, poly, rbf, sigmoid, precomputed <br />
b.	balanced_SVM : True or False , True if we want to keep class weights in order to to balance the classes depending on number of instances of classes present  <br />
6.	Change values of parameters in MLP_classifier_config.yaml file <br />
a.	hidden_layer_sizes_MLP : tuple giving number of neurons in each hidden layer in sequence  <br />
b.	learning_rate_init_MLP : learning rate used in algorithm to learn the MLP  <br />
c.	max_iter_MLP : maximum number of iterations used in learning MLP <br />
7.	Change values of parameters in test_config.yaml file  <br />
a.	row_from_author_data : list of rows on which we would like to test our tf-idf based classifiers. It should be between 0 to 248. <br />
b.	test_question : question given by user to classify using tf-idf classifier  <br />
8.	Run model_tfidf_final.ipynb with all parameters set before. We get train and test accuracy for both the classifiers. If we have kept author_data_choice param True then we will also get author test data accuracy. It will also print the predictions of questions given in test_config.yaml file. <br />
### Classification using word2vec embeddings  <br />
We are using two classifiers , SVM (Support Vector Machine) classifier and MLP (Multilayer perceptron or simple neural network with n hidden layers) <br />
9.	Change values of parameters in SVM_classifier_config.yaml file <br />
a.	kernel_name_SVM : kernel used to build SVM like linear, poly, rbf, sigmoid, precomputed <br />
b.	balanced_SVM : True or False , True if we want to keep class weights in order to balance the classes depending on number of instances of classes present  <br />
10.	Change values of parameters in MLP_classifier_config.yaml file <br />
a.	hidden_layer_sizes_MLP : tuple giving number of neurons in each hidden layer in sequence  <br />
b.	learning_rate_init_MLP : learning rate used in algorithm to learn the MLP  <br />
c.	max_iter_MLP : maximum number of iterations used in learning MLP <br />
11.	Change values of parameters in test_config.yaml file  <br />
a.	row_from_author_data : list of rows on which we would like to test our word2vec based classifiers. It should be between 0 to 248 <br />
b.	test_question : question given by user to classify using word2vec classifier  <br />
12.	Change values of parameters in word2vec_config.yaml file <br />
a.	vector_size  : The number of dimensions of the embeddings. Preferred 100 to 800. <br />
b.	window : The maximum distance between a target word and words around the target word. Preferred 3 to 5.  <br />
c.	min_count : The minimum count of words to consider when training the model; words with occurrence less than this count will be ignored. Preferred 3 to 5.  <br />
d.	sg : 0 – use CBOW continuous bag of words model, 1 – use skip gram model to train word2vec model <br />
e.	train_new_word2vec : if word2vec model needs to be trained again or not. Use false only when it is already trained with required data and vector size and model is saved.  <br />
f.	tsne_word : word for which we need to visualize word2vec similarities using t-SNE plot.  <br />
13.	Run model_word2vec_final.ipynb with all parameters set before. We get train and test accuracy for both the classifiers. If we have kept author_data_choice param True then we will also get author test data accuracy. It will also print the predictions of questions given in test_config.yaml file. <br />
 
