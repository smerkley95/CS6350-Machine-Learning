1. Load your dataset using Pandas. Once the dataset is loaded into a Pandas DataFrame, add the names = columns (where columns is the column names for the dataset.)

2. Create a Perceptron object. (ie. p = Perceptron())

3. Standard Perceptron:
    a. Use the p.standard_train() method and input your X_train and y_train datasets. (ie. p.standard_train(X_train, y_train))
    b. Set up your test datasets, use the p.predict(X_test) to get back an array of all the predicted values.
    c. Set correct = sum(y_test == p.predict(X_test)) to see what the percent correct of the predictions was.

4. Voted Perceptron:
    a. Use the p.voted_train() method and input your X_train and y_train datasets. (ie. p.voted_train(X_train, y_train))
    b. Set up your test datasets, use the p.predict(X_test) to get back an array of all the predicted values.
    c. Set correct = sum(y_test == p.predict(X_test)) to see what the percent correct of the predictions was.

5. Averaged Perceptron:
    a. Use the p.averaged_train() method and input your X_train and y_train datasets. (ie. p.averaged_train(X_train, y_train))
    b. Set up your test datasets, use the p.predict(X_test) to get back an array of all the predicted values.
    c. Set correct = sum(y_test == p.predict(X_test)) to see what the percent correct of the predictions was.
