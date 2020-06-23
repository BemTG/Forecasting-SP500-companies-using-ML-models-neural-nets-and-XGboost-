# Stock-market-forecasting-neural-net-and-XGBoost-models-
How markets are tracked and forecasted?
Correlation 
Many investment banks and hedge funds around the world trade stocks to make money for their investors.  When it comes to trading the main goal is to preserve money and essentially take trades when odds are in ones favour. There are several ways a hedge funds or an investment bank ends up making a trade, one of the many is through quantitative research and analysis.
What do quantitative traders in hedge funds do?
Quantitative traders use data to make predictions about the future. This is usually carried out by making simple models to capture the markets state and forecasting out based on previous historical patterns/ behaviour of the market. Quants find patterns in these historical datasets and make risk adjusted statistical bets based on the patterns and behaviour of the market. 
Some hedge fund may incorporate simple models such as the Capital Asset Pricing Model (CAPM) to describe the relationship between systematic risk and expected return of a stock to help execute a trade.
 
r= βr(t)+α(t)         


The total return of a stock can be explained using the two variables, market return and residual return. β is simply a measure of how correlated the given stock returns are to the market whereas α is the residual returns attributed to the stock irrespective of the market returns. 
Quant traders build strategies and models to predict the alpha factor of the given stock in order to take market neutral trades. The goal is choose stocks that will over perform when market goes up and to choose stocks that do not underperform as much when markets goes down.  
Hedge funds will use a combination of different models (including machine learning models) to predict if the given stock is going to be above or below the market. Based on these predictions traders can take trades that are independent of the market returns.
Simple example of market neutral trade :
r(p)=W_A*β_A+ W_B*β_(B     )  + 〖    W〗_A*α_A+W_B*α_B

Let assume our predictive model is forecasting that stock A is going to increase by 1% above the market. In order to take a neutral trade we would have to find a stock that is inversely correlated to the market. As a result, we find that stock B will be trading -0.5% below the market. Since we cannot change the  β values of the stock we would have to adjust the weighting (W_A  & W_B) accordingly to reduce market exposure to zero. For this specific example if stock A has β_A=1 and stock B is β_(B  )=-1 , then W_B would have to be 4 whenever  W_A is 2. Consequently, the expected return r(p) is going to derive from solely from the alpha factors and hence will be neutral from the market returns.
It is important to realise that hedge funds spend substantial amount of money constructing, developing and improving the predictive models since inaccuracy in the model can lead to considerable amount of losses. Even 1% increase in model performance is worth exploring when managing millions or billions of dollars.
How does the model in the webapp work?
The model in webapp  is a neural net supervised machine learning model that has been trained with 5 years of historical data. This model primarily takes the historical adjusted close values from yahoo finance of the selected stocks and forecasts the upcoming 5th day value.
The way a neural network works is it takes in inputs, which are processed in hidden layers with weights that are adjusted/updated during training. This is followed by the model yielding an output or a prediction based on the patterns and relationship it captured during training period. 
The user does not necessarily need to specify what patterns to look for, once constructed the model architecture and adjusted the learning parameters, the neural network learns on its own. 
Since our data is relatively small we used a simple model architecture of 2 hidden layers with 5 dense nodes. The activation function we have used for the node is relu (rectified linear unit) which is a nonlinear. By stacking several of these dense nodes we can create higher order of polynomials which help capture the patterns of the dataset. Thus the more layers we add, the more complex mathematical functions we can model and fit. 

The data was split 67% for training and 33% for testing. We trained our small dataset for 3 epochs, which is the number of times the model will cycles through the data. We measured the loss of the model using mean squared error which was calculated to be ~19% (the closer to 0 the better). 
For more information about the project and the source code click the github link.
Improvements 
There is certainly a lot of room for improvement, one of which is to add more market features to dataset such as RSI, Bollinger band and moving averages when training the model. This can lead to decrease the loss in the model. 
Moreover, we are not retraining the model overtime hence it is possible for model to diverge from optimal weights as new data points come in.
When using regression models it is tough know how long to keep the trade but that’s when we can look into implementing reinforcement learning to make an agent which can take actions based on the optimal policy.
