Instructions for Code:

    1. Load your dataset using Pandas. Once the dataset is loaded into a Pandas DataFrame, add the names = columns (where columns is the column names for the dataset.)

    2. For AdaBoost:
        a. First create an instance of an AdaBoost object. Specify the number of stumps you would like the object to have. AdaBoost(t_stumps = n)

        b. Next, call .fit() on that object, giving the data you would like to train the model with. .fit(df.drop('y', axis = 1).values, df.drop('y', axis = 1).columns.tolist(), df['y'].values). This allows the code to fit to the dataset.

        c. Last, call .predict() and use the data you would like to test the model with. Like .predict(test_data_df).

        d. Additionally, you can see how many were correct by first .predict(test_data_df) == test_data_df['y'].values, and then summing the resulting list.


    3. For Random Forest:
        a. First create an instance of an RandomForest object. Specify the number of trees you would like the object to have. RandomForest(n_trees = n)

        b. Next, call .fit() on that object, giving the data you would like to train the model with. .fit(df.drop('y', axis = 1).values, df.drop('y', axis = 1).columns.tolist(), df['y'].values). This allows the code to fit to the dataset.

        c. Last, call .predict() and use the data you would like to test the model with. Like .predict(test_data_df).

        d. Additionally, you can see how many were correct by first .predict(test_data_df) == test_data_df['y'].values, and then summing the resulting list.

        e. Note: my code also plots the percent calculated correctly.
