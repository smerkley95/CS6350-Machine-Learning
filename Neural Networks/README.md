Load your dataset using Pandas. Once the dataset is loaded into a Pandas DataFrame, add the names = columns (where columns is the column names for the dataset.)

Create a NN object. (ie. nn = NN())

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


Then you train the neural network by using nn.train(X, y).

    # Create a NN
    nn = NN(layer_sizes = [10, 10, 1], learning_rate = 1)
    nn.train(X_train, y_train, epochs = 100)

    correct = np.sum((y_test == nn.predict(X_test).reshape(1, -1)[0])) / len(X_test) * 100
    print(f"Percent Correct: {correct:0.3}%")


For analyzing different numbers of nodes to see the percents correct you can implement code like this:
    
    percent_correct = []
    num_of_nodes = [5, 10, 25, 50, 100]
    
    for nodes in num_of_nodes:
      nn = NN(layer_sizes = [nodes, nodes, 1], learning_rate = 1)
      nodes_percent_correct = []
      for i in range(10):
        # Create a NN
        nn.train(X_train, y_train, epochs = 100)

        correct = np.sum((y_test == nn.predict(X_test).reshape(1, -1)[0])) / len(X_test) * 100
        nodes_percent_correct.append(correct)
    
      percent_correct.append(np.average(np.array(nodes_percent_correct)))
    
    for i in range(len(num_of_nodes)):
      print(f"{num_of_nodes[i]} nodes: {percent_correct[i]:0.3}%")



