Instructions for Code:

    1. Load your dataset using Pandas. Once the dataset is loaded into a Pandas DataFrame, add the names = columns (where columns is the column names for the dataset.)

    2. For Batch Gradient Descent:
        a. First make sure to normalize the data by subtracting the mean of every column and then dividing by the standard deviation. This will allow the data to all be on the same scale.

        b. Next, call the Batch_Gradient_Descent function. For this, I usually set X = df.drop('y', axis = 1).values, y = df['y'].values, and the learning_rate = 0.01 to start.

        c. This will give you back the weights and cost_over_time.

        d. Next you can calculate the cost using the Cost_Function function. To do this you will again give X and y like above but then you will also give the weights that you received from the Batch_Gradient_Descent function.

        e. This will give you all the information I have used for this part of the assignment.

        f. Note: my code also plots the Cost Function per Iteration as well.


    3. For Stochastic Gradient Descent:
        a. All you need to do for thisis use the same data that was loaded before, call the Stochastic_Gradient_Descent function where again, X = df.drop('y', axis = 1).values, y = df['y'].values, and the learning_rate = 0.01 to start.

        b. Also set the iterations, I set it to 100 for this example.

        c. This code will return the weights and the cost.

        d. Note: again, my code plots the Cost per Number of Updates.


    4. Lastly, this code also shows the weight vectors for the Batch Gradient Descent, Stochastic Gradient Descent, and the Optimal Weights and prints them so they can be compared.
