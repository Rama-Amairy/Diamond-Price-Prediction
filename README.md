# Diamond-Price-Prediction
Diamond Price Prediction is a linear regression problem predict the market price in US dollars of a diamond by using the data-set I have (the price depended on the diamond features).
Diamond Price Prediction
Framing the Problem
The diamond is very rare precious stone and therefore Diamonds are considered to be Very Costly.
Some big company need to know the updated market price (in US dollars) of any diamond it sells. This is a classic regression (i.e., evaluation) problem, in which I need to collect the relevant data, build a useful model and estimate the expected error.
So, I need to build a model which predicts the market price in US dollars of a diamond by using the data-set I have (the price depended on the diamond features).
Have a high-accuracy with smallest mean square error is our goal.
EDA
1-	Analyze data-set :
•	Carat Weight: 0.2Kg - 5.01Kg
•	Cut: Describe cut quality of the diamond Fair, Good, Very Good, Premium, Ideal
With a Higher Cut Quality, the Diamond’s Cost per Carat Increases.
This is because there is a Higher Wastage of the Rough Stone as more Material needs to be Removed in order to achieve better Proportions and Symmetry.
•	Color: from J (Worst) to D (Best)
The Color of a Diamond refers to the Tone and Saturation of Color, or the Depth of Color in a Diamond.
The Color of a Diamond can Range from Colorless to a Yellow or a Faint Brownish Colored hue.
Colorless Diamonds are Rarer and more Valuable because they appear Whiter and Brighter.
•	Clarity: clearness I1 (Worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (Best)
•	Depth: The Height of a Diamond, measured from the Culet to the table, divided by its average Girdle Diameter.
•	Table: The Width of the Diamond's Table expressed as a Percentage of its Average Diameter.
•	Price: Price of the Diamond.
•	X: length in mm (0--10.74)
•	Y: width in mm (0--58.9)
Z: depth in mm (0--31.8).
Categorical: Cut, Color, Clarity.
Numerical: Carat, Depth, Table, Price, X, Y, Z.
Target: price
 
2-	Cleaning data: 
•	drop the Id column as we already have Indexed dataframe.
3-	Visualization data:
•	Start in correlation between features draw the heatmap and sort the corr with price: the positive correlation between the carat and price is the highest (0.92) and the carat with x,y,z is (0.98), there is a (negative correlation between the table and culet and with the price and depth[small negative correlation because in the same depth there is different price]), and for the dimensions As the Dimensions increases, Obviously the Prices Rises. For numerical values
•	Correlation between categorical values in three features is positive as the information about diamond.
•	Outliers: in the first correlation (price and carat) there is 21 outlier values. And the relation between them Exponentially.
•	categorical value: we see that the premium cut is the most expensive followed by vary good and the ideal is most common, color is already sorted by the price and the most common color is G, for Clarify It seems that VS1 and VS2 affect the Diamond's Price equally having quite high Price margin and the most common is SI2, SI1.
•	distributions: we use hist plot to check the distribution of the target variable 'price' and whether it follows a normal distribution or not. A normal distribution is important for many statistical methods, including linear regression, which is a common modeling technique.

•	The first line sns.distplot(df['price'], fit=norm) creates a histogram and a density plot of the 'price' column using Seaborn's distplot function. The fit=norm parameter specifies that the plot should also show a normal distribution curve, which helps visualize how closely the data fits a normal distribution.
•	The next block of code calculates the parameters of the fitted normal distribution curve. norm.fit(df['price']) uses the fit method of the scipy.stats.norm object to estimate the mean and standard deviation of the normal distribution that best fits the data.

•	The final block of code creates a legend for the plot, showing the values of the mean and standard deviation of the fitted normal distribution. It also generates a QQ plot using stats.probplot function from the scipy.stats module, which helps to visually assess whether the data follows a normal distribution or not.
Preprocessing Data
•	x,y,z:  there is 17 sample with incorrect values x,y,z =0 we will drop it 
•	outliers: replace all outliers with Nan
•	convert categorical value: using Label Encoder because the values are sorted.
Feature Engineering 
•	add volume column: Create New Feature 'Volume' from x y z. and the relation between volume and price is positive correlation.
•	drop unneeded column: x,y,z
Feature Scaling
•	scaling numerical value: split the training data for train and validation and then fit transform the train data using standard Scaler and transform for validation.
Modeling
•	start with Linear Regression and we got the rmse is = 939.9 and it is not good result and the score =88%
•	trying mor complex model like Decision Tree Regressor rmse is=502.6 it is better than linear model and the score= 96% I think it is high but this is the best result? Let see cross validation score and try new model
•	trying random forest and the rmse is= 391.7, the score= 98% great result
•	xgb_model we get the rmse = 380.35 , the score = 98% So it’s better than uses random forest 
 





