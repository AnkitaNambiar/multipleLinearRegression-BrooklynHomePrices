# multipleLinearRegression-BrooklynHomePrices

# Model Creation

To answer if Brooklyn home purchase prices changed between Quarter 3 (Q3) and Quarter 4 (Q4) in 2020, I created a price predictor model to analyze the Q3 to Q4 shift. My Brooklyn home price predictor model for this business case originated from a previous Brooklyn home price predictor model I created from data on real estate purchases within the borough of Brooklyn from 2016-2020. My previous model met all the conditions for predictive accuracy, so I decided to include the 2 predictor variables I had in my new model: gross square feet and neighborhood. Along with the predictor variables, I used the same filters that worked for my previous model, ex: only prices between $6K to $6M. I kept only 2020 data in Q3 and Q4 since those are the periods we are focusing on. I then created a new column for Quarter in the dataset, made it a ‘character’ type, and added it as a categorical variable into my price predictor model.

The final Brooklyn home price predictor model uses the following 3 predictors: gross square feet, neighborhood, and quarter. The regression output for this model has promising qualities. The residual standard error (RMSE) was 443400, the multiple R-squared is 0.7219, and has 39 degrees of freedom. These values show that the Brooklyn home price predictor model for Q3 and Q4 of 2020 has high predictive accuracy, so we can feel confident in the model’s predictive power and proceed in using it to answer if Brooklyn home purchase prices changed between Q3 2020 and Q4 2020.

# Quarter

With the regression output of the Brooklyn home price predictor model, I analyzed the effects of Quarter on price. The p-value for Quarter is 0.011314, meaning that there is a statistically significant difference between the home prices in Q3 and Q4. Furthermore, the regression coefficient for Quarter is 80877.71, so, on average, a home price in Q4 was $80,877.71 more expensive than a home price in Q3. This reveals a significant additive change from Q3 to Q4. This $80877.71 increase is of course assuming the other predictor variables were kept constant, so we must do a deeper dive into possible interactions between quarter and the other predictor variables – neighborhood and gross square feet – on price.

<img width="553" alt="Screenshot 2023-01-27 at 1 54 28 PM" src="https://user-images.githubusercontent.com/105748980/215184906-ba11da4e-f9a2-45f0-83e4-7c57123ffc9b.png">

# Neighborhoods

For the predictor variable neighborhood, I determined the neighborhoods that have the most significant relation with price, as those with the smallest p value which were < 2e-16. Overall, 27 neighborhoods had a significant relation with price, however, I decided to stick with the 5 most significant for simplicity: Brooklyn Heights, Downtown Fulton Ferry, Park Slope, South Ocean Parkway, and North Williamsburg.
For the 5 most significant neighborhoods, I plotted the box plot “Brooklyn Home Prices for Neighborhoods with Significant Price Relations from 2020 Q3 to 2020 Q4,” below. As seen in the graph, from Q3 to Q4, home prices in Brooklyn Heights and South Ocean Parkway dropped. However, home prices in Downtown Fulton Ferry, Park Slope, and North Williamsburg increased. For Brooklyn Height, there was an approximate $3.1M price drop while, in North Williamsburg, there was an approximate $800k increase. This shows an effect of quarter and neighborhood on price, meaning neighborhood is important to consider for the price change between 2020 Q3 to 2020 Q4.

<img width="774" alt="Screenshot 2023-01-27 at 1 49 01 PM" src="https://user-images.githubusercontent.com/105748980/215184676-f6106c18-9817-4358-b3a6-97e33ea524d2.png">

# Gross Square Feet

For the predictor variable gross square feet, I found gross square feet had a significant relation with price, with a p-value of < 2e-16.
I then created the "Brooklyn Home Price based on Gross Square Feet for 2020 Q3 to 2020 Q4” plot, below. The graph shows how price increases with greater square feet, which is expected. More importantly, when comparing the linear regression lines of Q3 and Q4, we see that Q4 homes were sold at higher prices than Q3 for the same square feet. The difference in price between the quarters is present for all square feet but gets larger as square feet increases, seen in the not parallel linear regression lines of Q4 and Q3. At 2000 square feet, there is an approximate $100k increase from Q3 to Q4, while, at 6000 square feet, there is an approximate $400k increase. There is an effect of quarter and square feet on price, signaling that square feet is important to consider for the price change between 2020 Q3 to 2020 Q4.

<img width="747" alt="Screenshot 2023-01-27 at 1 48 54 PM" src="https://user-images.githubusercontent.com/105748980/215184715-ecdfcea4-452b-4074-a8d7-28585e4d1834.png">

# Limitations

My price predictor model, as stated, uses linear regression to explain Brooklyn housing prices, so I checked whether the assumptions made by the linear regression model are met or not. First, I checked the linearity of the data with a Residual vs Fitted Plot, below. There is a clear pattern in the points, so the assumption that there is a linear relationship between price and the predictor variables is not met. Second, I tested the homoscedasticity with a scale-location plot, below. In the scale-location plot, the points are not equally spread, so there is a heteroscedasticity problem and we do not meet the homoscedasticity assumption.

Third, I checked the normality of the residuals with a QQ plot of the residuals, above. In the QQ plot, the majority of the points fall approximately along the reference line, so the normality assumption is met. However, there are deviating endpoints, which suggest a skewed distribution. Fourth, I checked that the predictors are independent using the Durbin-Watson test. I found a p-value of 0, so we conclude that the residuals in this regression model are autocorrelated and fail to meet our independence assumption. Fifth, I tested the independence of errors with a Residual vs Fitted Plot, above. In the plot, there is a slight correlation, so the independence of errors is not met. Overall, the majority of the Ordinary Least Squares (OLS) assumptions are not met, meaning that remodeling is necessary. A possible remodeling step is using a logistic transformation on price.

<img width="995" alt="Screenshot 2023-01-27 at 1 48 46 PM" src="https://user-images.githubusercontent.com/105748980/215184542-cb0d3289-039d-4fcd-b358-c9284432938f.png">

# Conclusion

With my price predictor model, I found that Brooklyn home purchase prices significantly changed between Q3 2020 and Q4 2020 with an additive increase of $80,877.71 from Q3 2020 and Q4 2020. This was supported by the increase in price for all square footage from Q3 to Q4. However, we cannot apply this insight to all of Brooklyn because while overall Brooklyn home purchase prices increased, in certain neighborhoods there was a price decrease. Neighborhood should be accounted for to determine the price change between Q3 2020 and Q4 2020. Furthermore, the model did not meet all the OLS assumptions, so the results found should not be fully trusted and used for business decisions. The next steps include remodeling and considering a non-linear regression model to determine if Brooklyn home purchase prices significantly changed between Q3 2020 and Q4 2020.
