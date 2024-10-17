Dataset Description:

The data consists of e-commerce products. Each product has a unique id and a category. My goal is to predict the category of each product based on categorical features, a noisy text description and a noisy image. Total number of products are 43255. 

Data fields:

id: a unique id for each product

category: a string describing the category of each product

gender: a string describing the target gender for this product

baseColour: the base colour of this product (note that the base colour may be different than the colour in the image of this product)

season: a string describing the target season for this product

usage: a string describing the target usage for this product

noisyTextDescription: a string of words corresponding to a noisy display name of the product

Images: For each product, there is a noisy image of the product in the directory "noisy-images". The filename of each image is the product id. The images are 60x80x3 jpeg images in RGB format (i.e., each pixel intensity is an integer in {0,1,2,…,255}).

Model training process:

0. Preprocess dataset including one-hot encoding for labels, data augmentation, etc.
1. Use CNN to classify images
2. Append text features "gender" "basecolor","season","usage" together with "noisy text" into one text feature
   Then, use LSTM to classify combined text feature based on sentence to tensor function (break down into letters, digits and punctuation)
3. Use simple neural network to concatenate results from RNN and CNN, and output into sigle probability as final result
4. Use trained model to predict test set and output the result as "submissing_final.csv".

Result: 

Test accuracy for each part of dataset (images, texts, features) is from 87% to 91%, after train a neural network to ensemble all the informatiion the final test accuracy is boosted to 95%! 
