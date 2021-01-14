Concrete is generally made of three ingredients: cement, water and aggregate. In many cases different types of aggregate are used. Since there is no standard for what aggregate should be used, many people create their own ratios of cement, water, and aggregates. The goal of this project is to look at how different ratios of these ingredients affect the compressive strength of concrete, and predict if the compressive strength of concrete will reach the minimum requirement for the American Concrete Institute(ACI). The analysis has implications for construction and safety. <br />
	The dataset is from  https://code.datasciencedojo.com/datasciencedojo/datasets/blob/master/Concrete%20Compressive%20Strength/Concrete_Data.xls. It has 9 variables and 1030 rows of data. Of the 9 variables, 7 of the variables are the materials that go into the concrete mix, one variable is the age of the concrete, and the last variable is the compressive strength of the concrete. There are many values of 0 for the material variables, meaning that there is zero amount of that material in the mix. The age of concrete is important because when concrete is mixed together a chemical reaction occurs which hardens the concrete and takes place over many months. After 7 days, concrete is said to have about 75% of its potential strength, over time it will continue to harden slower.<br />
	We add a column called “ACI Approved”. The ACI is the American Concrete Institute and is commonly used to set standards for concrete with over 400 standards for maintaining and manufacturing concrete. The ACI Approved column doesn’t fit all of these standards, but indicates a minimum compressive strength of 4500 psi or 31.026 MPa. In this data set, 60% of the concrete mixes reached the minimum compressive strength of 31.026 on the day they were measured. <br />
	We start by looking at the effect of the age of concrete on compressive strength. The points in **Figure 1** show the compressive strength of concrete in MPa by how many days old it is. The color of the points indicate the amount of water in the concrete mix. High concentrations of water can slow down the time it takes for the chemical reaction to occur. The dashed red line represents the minimum 31.026 MPa threshold that the compressive strength of the concrete must reach. In the first 30 days only 47% of the concrete mixes are classified as “ACI Approved” compared to 93% after 30 days. The colors of the points show how concrete mixes with less water will gain compressive strength faster with 63% of the concrete mixes, with less water than the mean of the data set, being “ACI Approved” within 30 days compared to 35% being approved of the mixes which have more water than the mean. <br />
	Next the dimensionality of the data is explored with a principal component analysis for the 8 variables. In **Figure 2**, the blue line shows that 5 columns captures 97% of the variance. The problem with the blue line is that variables like superplasticizer have small values compared to the other variables. The orange line, which is the same analysis but with standard scaling, shows the data can be reduced in dimensionality with only 7 components capturing 99.6% of the significant information.<br />
	We want to predict whether a mix of concrete will meet the ACI standard for compressive strength. We create a sklearn pipeline which has a StandardScaler and LogisticRegression. A 75%/25% train/test split is done. The model has an 88.8% accuracy. The recall of the model is 90.7%, and precision is 91.3%. <br />
	When creating concrete, it is important to know what materials have the most impact on a certain characteristic of the concrete. **Figure 3** shows the coefficient weights for each of the features used in the logistic regression. It is seen the most important factor for compressive strength is age. The more days after the concrete has been mixed, the stronger it gets. The most important material is cement, which is a critical component in the chemical reaction that makes concrete harden.<br />
	Overall, this analysis shows that 93% of concrete mixes will meet the standard set by the ACI for compressive strength at some point after 30 days. However, the age of the concrete alone will not guarantee an ACI approval as materials such as cement are a crucial component to creating concrete with a high compressive strength. <br />


![fig1](https://user-images.githubusercontent.com/55674235/104646132-a8516100-5675-11eb-8a30-b9522220095b.png) 
![fig2](https://user-images.githubusercontent.com/55674235/104646196-be5f2180-5675-11eb-9215-a394230a889e.png) 
![fig3](https://user-images.githubusercontent.com/55674235/104646195-bdc68b00-5675-11eb-8a68-65d3380acf7f.png)


