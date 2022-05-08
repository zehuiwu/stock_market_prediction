# stock-market-prediction

## Project description

Stock price prediction is a hot research topic. Given the arising of Deep Learning, many researchers are now trying to use Deep Learning techniques to do sotck price prediction. The stock markets are complex, non-linear and chaotic, which is not able to be estimated by Linear Models. However, Deep Learning is very good at dealing with non-linearity. We aim to use the information such as price of past 5 days to predict the next day's price, which is similar to a regression. In our project, we propose a model, which outperforms the trivial prediction and other models a lot, to predict the stock price and help our trading strategy.

The trivial prediction is introduced in our presentation, and a brief visualization is:


The tivial prediction of Apple stock from 2017 July to 2020 July:

![image](https://user-images.githubusercontent.com/97364054/167312893-f36250a4-3310-43ca-90ed-5508514b1c05.png)

Looks good? Becasue we squeeze the time window so that the gap between prediction and real price is not observable !

What about a GAN model proposed by the GAN paper [4]? 

![image](https://user-images.githubusercontent.com/97364054/167312936-4c8c30d2-bc7e-405a-b13c-f3981c8985e6.png)

 It looks like it does not even surpass the trivial prediction!
 
 Let's look at the loss:
 
 The trivial prediction is:
 
![image](https://user-images.githubusercontent.com/97364054/167312996-f88b91c4-497e-4502-96d2-ae1a53189c9a.png)

However, the GAN model introduced by the paper has higher RMSE!

![image](https://user-images.githubusercontent.com/97364054/167313077-d7e1480a-94fa-476e-b5d8-0ebf147ab123.png)


# Repository description
Inside the data folder, there are four subdirectories: EOD, hourly, pca_features, and vae_features. The EOD folder contains all the raw data (two-year stock prices for 6 stocks) downloaded from Yahoo Finance and the data after adding technical indicators. Inside the hourly folder, we collect the two-year hourly data for each stock. We cuurrently have not used these data in our model. The folder pca_features, and vae_features contain the features extracted in the pca_features_extraction, and vae_features_extraction notebook. There are several hyperparameters that can be changed in those notebook to produce different sets of features.

The Ml_models folder contains the training notebooks for ml models. To reproduce the results or use other dataset, change the path for data in these notebooks. 
The dl_models folder contains the training notebooks for dl models.

# Reference

[4]Sonkiya, Priyank, Vikas Bajpai and Anukriti Bansal. “Stock price prediction using BERT and GAN.” ArXiv abs/2107.09055 (2021): n. Pag.
