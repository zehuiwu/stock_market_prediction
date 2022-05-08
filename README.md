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
Inside the data folder, there are four subdirectories: `EOD`, `hourly`, `pca_features`, and `vae_features`. 

The `data_extractions` contains codes getting hourly data and sentiment data, but they are not used. You may ignore.

The `feature_ops` contains files extract and expand features. However, we have uploaded both raw datas and expanded datas.

The `EOD` folder contains all the raw data (two-year stock prices for 6 stocks, in addition 12-year for apple) downloaded from Yahoo Finance and the data after adding technical indicators. Inside the hourly folder, we collect the two-year hourly data for each stock. We cuurrently have not used these data in our model. The folder `pca_features`, and `vae_features` contain the features extracted in the `pca_features_extraction`, and `vae_features_extraction` notebooks in the 'feature_ops_notebook' folder. There are several hyperparameters that can be changed in those notebook to produce different sets of features.

The `Ml_models` folder contains the training notebooks for ml models. To reproduce the results or use other dataset, make sure the path for data is correct in these notebooks. Files' name are as in notebooks, just change path. 

The `dl_models` folder contains the training notebooks for dl models. The `LSTM and MLP.ipynb` file contains training and visualization. You may view it directly, or directly download and run it. Whenever you see file_name varaible or any load() function, please make sure path is correct. The name of file is as provided. The `Transformer Stock.ipynb` contains model training and visualization, but output is cleaned out because there are too many outputs to open in github. In `Transformer Stock Graph.ipynb`, there are full visualization. The saved model of transformer is too large to be uplaoded in github, you may request throgh email if you need. To run them, just run the training file, it contains visualization after you run. The `Transformer Stock Graph.ipynb` file is for visualization purpose only.


# Commands to excecute codes
Since we are using notebooks, there is no need to run any command. You only need to download everything

# Reference

[4]Sonkiya, Priyank, Vikas Bajpai and Anukriti Bansal. “Stock price prediction using BERT and GAN.” ArXiv abs/2107.09055 (2021): n. Pag.
