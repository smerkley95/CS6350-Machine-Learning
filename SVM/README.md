Load your dataset using Pandas. Once the dataset is loaded into a Pandas DataFrame, add the names = columns (where columns is the column names for the dataset.)

Create a SVM object. (ie. svm = SVM())

Set up your datasets like so:

    columns = ["Variance", "Skewness", "Curtosis", "Entropy", "Label"]
    bank_note_train = pd.read_csv(Download_From_Google_Drive('1Du3SiMaZGn-HuvFUJchE6NNwiIdRlQbh'), names = columns)
    bank_note_test = pd.read_csv(Download_From_Google_Drive('1mX8lXt2TvYGyDBihyGOTMnYRiGdzeoKr'), names = columns)

    # Training Datasets
    X_train = bank_note_train.drop('Label', axis = 1).values
    y_train = bank_note_train['Label'].values
    
    # Testing Datasets
    X_test = bank_note_test.drop('Label', axis = 1).values
    y_test = bank_note_test['Label'].values


Then you can set up your learning rate schedule to take in a value of t and preseting the values for gamma. Then you train the linear model by using svm.train(X, y).

    def Learning_Rate_Schedule(t):
      gamma_0 = 9.5
      a       = 3.5
      return gamma_0 / (1 + gamma_0 / a * t)
    
    lrs_1 = []
    for c in C:
      svm = SVM(C = c, learning_rate_schedule = Learning_Rate_Schedule)
      svm.train(X_train, y_train)
    
      print('\nWeights:', svm.weights)
      print('Bias:', svm.bias)
      correct = sum(y_test == svm.predict(X_test))
      print(f"Percent Correct: {correct / len(X_test) * 100:0.3}%")
      svm_prediction_error = correct / len(X_test)
      lrs_1.append(svm_prediction_error)


For the Dual Model you can set up your SVM object the same way, then train using svm.train_dual(X, y). Then you can get the alphas back using svm.dual_result.x. Also you can predict values using the formulation below.
    
    for c in C:
      svm = SVM(C = c)
      svm.train_dual(X_train, y_train)
      # print('\nResult:', svm.dual_result)
    
      alpha = svm.dual_result.x
      w, b = svm.get_weights_and_bias(X_train, y_train, alpha)
      print(f'C: {c}, Weights: {w}, Bias: {b}')
      correct = sum(y_test == svm.predict_dual(X_test, X_train, y_train, alpha))
      print(f"Percent Correct: {correct / len(X_test) * 100:0.3}%")
      correct = sum(y_test == svm.predict(X_test))
      print(f"Percent Correct: {correct / len(X_test) * 100:0.3}%")
      # svm_prediction_error = correct / len(X_test)


