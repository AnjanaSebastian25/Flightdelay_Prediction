# Flightdelay_Prediction

I.THE PROBLEM TO SOLVE
The business problem I have taken for the analysis is that an organ donor who needs to send an organ urgently from BWI airport (Baltimore) to a New York Airport on a Monday so the patient who will receive that organ can have his surgery done that same day with the least delay as possible. To do this the organ can be shipped through OH carrier that reaches JFK airport, or use RU carrier that reaches Newark airport. So, I must decide by reducing the chances of flight delays of each option.
II.DATA USED
I have used the Flight Delay dataset. The attributes used in the dataset are:
Departure time, carrier, destination, distance, flight date, flight number, origin, Iather, day of the Iek, day of the month, tail number of aircraft, and flight status.
III.CLEANING THE DATA
Before I started the analysis, I make some data pre-processing. Since the data set contains data of flights which departure from different airport, and I only want to predict the delay of the flight from Baltimore airport to New York airport, to make the analysis easier, I dropped all the flights data which is not departure from BWI airport.
After I clean the data, I do some visualization about the dataset and get an overview of attributes. First, I describe the dataset to see if there’s any unusual data or missing value, the dataset has a good condition and free with missing value.
Then, I want to know what’s the delay rate of both carrier, so I draw a scatterplot and color the point base on if the flight is on time or not. 

Then I draw the heat map to check the correlation betIen attributes, I can see there are two groups of attributes are highly correlated, which are CRS_DEP_TIME and DEP_TIME, DISTANCE and FL_NUM.
To choose the right carrier company, I want to know both frequency and delay rate of these two companies, so I draw the histogram about the frequency and delay rate based on the carrier. It shows RU company has more flight than OH, hoIver the average delay rate of RU is also relatively higher.

IV.ANALSYIS
Naïve Bayes Classifier
After I know the dataset through statistics and visualization, I run both algorithms to make prediction. I first run the Naives Bayes Classifier, for that I will built the classifier model with fthe predictors which are DAY_IEK, CRS_DEP_TIME, DEST, CARRIER, and I separate 60% data as training set and 40% as testing set. After I build the model, according to the predictions, the OH carrier flight on Mondays towards JFK is predicted to be ontime. On the other hand the RU carrier flight on Mondays to EWR is predicted to be delayed. Therefore, on a Monday it would be better to use the OH carrier towards JFK, instead of the RU carrier that flies to EWR
However, I notice that it's strange to see that RU carrier to EWR is predicted to be delayed when all 4 flights Ire actually ontime. I think it happens because in the training models, most of the flights covering this route by this airline. So, I run the model again with testing data instead of valid data, and this time I get a better result.
KNN Algorithm
Now I analyse the flight delays dataset using KNN algorithm. For the convenience of using the dataset for the algorithm, I have taken only the data of flights starting from BWI to JFK and EWR on Monday and use only the following columns: CARRIER, DEP_TIME, DAY_IEK, DAY_OF_MONTH and Flight Status. After that I add an index column named number to the dataset which acts an ID for each row, and I rename the column DAY_IEK as DAY_OF_IEK for better understanding for the variable. Then I create dummy variables for CARRIER column as KNN cannot be applied directly to categorical predictors. As KNN calculates distances, I can use only numeric variables as the predictors.
Then I split the dataset in to training and validation sets. The training set accounts for 60% and the validation set accounts for 40% of the total. First I create a model to classify the flight status of OH carrier on Monday Of 10th at 15:40 PM. I transform the entire dataset by normalizing to make everything to the same scale as the features are on different metrics. Then I use K nearest neighbthe algorithm against the normalized data with k =3. After that I train the classifier for different values of K and I choose K = 5 based on the accuracy of the model. Then I retrain the entire dataset with K=5 and use KNN. According to KNN classifier the OH carrier is predicted to be on time.
After that I use KNN algorithm to create a model to classify the flight status of RU carrier at the same day and same time as the OH carrier I classified before. Following the same steps as above, the RU carrier is predicted to be delayed.
V. CONCLUSION
I can conclude that OH carrier can be used to transport the organ from BWI to JFK on Monday. Both models classify that the OH flights leaving on Monday from BWI will be on time. Therefore, I suggest that the organ should be shipped in an OH carrier.
REFERENCES
[1]StackOverflow: How to delete rows from a pandas DataFrame based on a conditional expression | StackOverflow. (2021, January) M. Ghenis. https://stackoverflow.com/questions/13851535/how-to-delete-rows-from-a-pandas-dataframe-based-on-a-conditional-expression
