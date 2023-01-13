# s23-winter-proj

Jayne Bottarini
bottarin@usc.edu

This project provides an artificial intelligence model to distinguish between sarcastic and real news headlines. Using a pre-trained BERT model, I was able to encode each of the headlines and develop a model to perform NLP efficiently.

For this project, I used Kaggle’s News Headlines Dataset for Sarcasm Detection. This dataset has three main attributes: is_sarcastic (whether or not the headline is intended to be sarcastic), headline (the name of the actual headline given), and article_link (the url to the online article). The dataset drew from two major news sources: the Huffington Post for real headlines and the Onion for sarcastic headlines. 

With BERT, there were no major reductions I had to do to the size of the dataset. In preprocessing, the most important thing was dropping the article_link column because it was unnecessary data that could have resulted in a much longer training process. The only other processing I did on the dataset was some calculations on the longest and average length of headline for padding purposes when building the model.

For this model, I chose to use a pre-trained BERT because NLP problems can take a very long time to train and test on their own. A pre-trained model significantly reduces the amount of time spent, and I am able to fine-tune some parameters directly. Fine-tuning provides the opportunity for the model to be adapted to different kinds of tasks beyond binary classification. 

Within the model, I used keras layers to build the neural network. Each layer was Dense, which means each neuron takes in every input from the previous layer. While more computationally expensive, the Dense layer provides a faster training process, which was one of the goals for this project. Because I wanted the opportunity to fine-tune and adjust different hyperparameters in the model, a quick training process was essential to having the time to go back and readjust.

Some hyperparameters I chose to fine-tune was the learning rate, which I increased to the value as advised by BERT and the number of epochs, which I decreased to 2. I also tried to increase the max length of each tokenized headline (increase the amount of padding) to try to incorporate more datapoints into training. However, increasing the padding too much resulted in a lower accuracy level.

For the first epoch, the model achieved a 0.5776 accuracy and a 1.0029 loss, and the second epoch achieved a 0.5265 accuracy and 0.8085 loss. The final validation accuracy was 0.8435. These numbers could most definitely be improved, likely with more epochs and an adjustment to the max size of each headline.

Due to my current limitations, I think using pre-trained BERT is very fitting because it allows me to perform higher accuracy training in a shorter amount of time with limited GPU. What was most difficult about managing this project was that after a certain amount of idle time, Google Colab would restrict my GPU use and start over with a CPU. This made training hard to complete, but once I got GPU back, BERT was an excellent way to see quick results.

Beyond sarcastic/not sarcastic classification, this model could potentially be expanded for social good by adapting it to similarly detect real vs. fake news. In this case, however, a headline may not be enough, so the dataset would be much more difficult to handle. With a much larger dataset, my methods could be far too computationally expensive, especially with the tools available to me. I would also be interested to see if there was a method of determining political bias from a headline. 

My next steps to continue this project would be to look into a more diverse dataset, beyond just the huffington post to see if the model performs the same with a different news source. With this specific model, I would likely make more fine-tune adjustments and run with more epochs to see if anything more changes within the model.
