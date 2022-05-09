# Stock-Market-Prediction
By Zehui Wu and Zonglin Lyu
## Project description

Stock price prediction is a hot research topic. Given the arising of Deep Learning, many researchers are now trying to use Deep Learning techniques to do sotck price prediction. The stock markets are complex, non-linear and chaotic, which is not able to be estimated by Linear Models. However, Deep Learning is very good at dealing with non-linearity. We aim to use the information such as price of past 5 days to predict the next day's price, which is similar to a regression. In our project, we propose a model, which outperforms the trivial prediction and other models a lot, to predict the stock price and help our trading strategy. We tried out different techniques including tradidtional ML, MLP, LSTM, and finally find transformer can do well in this task.

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


## Repository description
Inside the data folder, there are four subdirectories: `EOD`, `hourly`, `pca_features`, and `vae_features`. 

The `data_extractions` contains codes getting hourly data and sentiment data, but they are not used. You may ignore.

The `feature_ops` contains files extract and expand features. However, we have uploaded both raw datas and expanded datas.

The `EOD` folder contains all the raw data (two-year stock prices for 6 stocks, in addition 12-year for apple) downloaded from Yahoo Finance and the data after adding technical indicators. Inside the hourly folder, we collect the two-year hourly data for each stock. We cuurrently have not used these data in our model. The folder `pca_features`, and `vae_features` contain the features extracted in the `pca_features_extraction`, and `vae_features_extraction` notebooks in the 'feature_ops_notebook' folder. There are several hyperparameters that can be changed in those notebook to produce different sets of features.

The `Ml_models` folder contains the training notebooks for ml models. To reproduce the results or use other dataset, make sure the path for data is correct in these notebooks. 

The `dl_models` folder contains the training notebooks for dl models. The `LSTM and MLP.ipynb` file contains training and visualization. You may view it directly, or directly download and run it. Whenever you see file_name varaible or any load() function, please make sure path is correct. The `Transformer Stock.ipynb` contains model training and visualization, but output is cleaned out because there are too many outputs to open in github. In `Transformer Stock Graph.ipynb`, there are full visualization. The saved model of transformer is too large to be uplaoded in github, you may request throgh email if you need. To run them, just run the training file, it contains visualization after you run. The `Transformer Stock Graph.ipynb` file is for visualization purpose only.


## Commands to excecute codes
Since we are using notebooks, there is no need to run any command on terminal, but just adjusting file path. You only need to go to the main page https://github.com/zehuiwu/stock_market_prediction, click on the 'code' icon, click 'download' and download everything. Then, you may upload the downloaded file to your notebook, and carefully go through file path. 

For example:

````python
X_train = np.load('C:/Users/KingO/JupyterProject/stock-market-prediction/data/pca_features/X_train.npy')
````

should be change to 
````python
X_train = np.load('Your-Path-of-X_train.npy')
````

Another example:

````python
file_name = 'AAPL_features.csv'
````

should become
````python
file_name = 'Your-Path-of-AAPL_features.csv'
````


## Results

Given our observation that many models does not surpass the trivial loss, we first calculate trivial loss as a pass-line for a model. Any model under that line is useless. For illustration purpose, we only use some graphs, while all visualizations are available in notebooks.

All hyper-parameters are shown in the notebooks

![b93397af2cfc839ed1551135b1f3aed](https://user-images.githubusercontent.com/97364054/167320259-9e13fc53-9df3-4f93-985b-1340212a6085.png)


### Combining 6 stocks and train with LSTM and MLP does not achieve pass-line:

![685ae3bca28e960291baa7a505e6cbe](https://user-images.githubusercontent.com/97364054/167320567-540aa9ed-9cca-4d35-a391-258921c099b0.png)

![5a348003f056fc4a56762d0f73ec824](https://user-images.githubusercontent.com/97364054/167320570-6208962c-78e6-438a-8b16-c4467b9af2e3.png)

### Training one stock each with LSTM and MLP are around pass-line, indeed they do trivial prediction:

![3df7828ae2a0212a06d3c0182ac89da](https://user-images.githubusercontent.com/97364054/167320715-1ccbe4cf-9d60-46b0-88ce-5ef7812039f0.png)

![5fc31f349bf7883061c73d642e0968e](https://user-images.githubusercontent.com/97364054/167320716-89f0a3e3-d291-4e93-b081-cf9e23433805.png)

### Traditional Machine Learning Model can surpass the pass-line a little:

![image](https://user-images.githubusercontent.com/97364054/167320765-3a3ed523-e2e2-4cef-ab85-67c03a85c221.png)

![image](https://user-images.githubusercontent.com/97364054/167320771-cf1b01d0-b00c-404b-b0d9-57f6d5bbc995.png)


### Transformer Model gives pretty good prediction:

![4269ecf26f8bc87a8fcc5036503bbb0](https://user-images.githubusercontent.com/97364054/167321303-87960586-d7d8-407a-8567-eceebd909192.png)


The intuition to use CNN to create a embedding of input and then pass to transformer is: after left padding, the output is the same shape with input, but each position contains information before and at that postion. Then, it can illustrate a 'shape' of time series rather than a single value. Plus, transformer has succeeded in NLP field which is also dealing with sequetial input, the performance is pretty good.

## Reference

Ivan Letteri, Giuseppe Della Penna, Giovanni De Gasperis, Abeer Dyoub: “A Stock Trading System for a Medium Volatile Asset using Multi Layer Perceptron”, arXiv:2201.12286 [q-fin.ST]

L. Chen, Z. Qiao, M. Wang, C. Wang, R. Du and H. E. Stanley, "Which Artificial Intelligence Algorithm Better Predicts the Chinese Stock Market?," in IEEE Access, vol. 6, pp. 48625-48633, 2018, doi: 10.1109/ACCESS.2018.2859809.

Kang Zhang, Guoqiang Zhong, Junyu Dong, Shengke Wang, Yong Wang, Stock Market Prediction Based on Generative Adversarial Network, Procedia Computer Science, Volume 147, 2019, Pages 400-406, ISSN 1877-0509, https://doi.org/10.1016/j.procs.2019.01.256.

Sonkiya, Priyank, Vikas Bajpai and Anukriti Bansal. “Stock price prediction using BERT and GAN.” ArXiv abs/2107.09055 (2021): n. Pag.

LI, SHIYANG, Xiaoyong Jin, Yao Xuan, Xiyou Zhou, Wenhu Chen, Yu-Xiang Wang and Xifeng Yan. “Enhancing the Locality and Breaking the Memory Bottleneck of Transformer on Time Series Forecasting.” NeurIPS (2019).
