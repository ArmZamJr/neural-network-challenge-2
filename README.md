# neural-network-challenge-2
Module 19 Challenge
``` # Create a StandardScaler ( I had help from TA on using correct values)
scaler = StandardScaler()

# Fit the StandardScaler to the training data
X_scaler = scaler.fit(X_train)


# Scale the training and testing data
X_train_scaled = X_scaler.transform(X_train)
X_test_scaled = X_scaler.transform(X_test)```

# Create a OneHotEncoder for the Department column
from sklearn.preprocessing import OneHotEncoder
department_encoder = OneHotEncoder(sparse_output=False)

# Fit the encoder to the training data
department_encoder.fit(np.array(y_train['Department']).reshape(-1, 1))

# Create two new variables by applying the encoder to the training and testing data
(Had help reshaping the encoder from fellow classmate)
y_train_enc_department = department_encoder.transform(np.array(y_train['Department']).reshape(-1, 1))
y_test_enc_department = department_encoder.transform(np.array(y_test['Department']).reshape(-1, 1))  

# Display results
print("Training Data Encoded Department:")
print(y_train_enc_department[:5])
print("Testing Data Encoded Department:")
print(y_test_enc_department.shape)

# Create a branch for Department
# with a hidden layer and an output layer
# Create the hidden layer
department_hidden = layers.Dense(units=32, activation='relu',name='department_hidden')(shared_layer2)


# Create the output layer
#department_output = layers.Dense(units=3, activation='softmax',)(department_hidden)
(Had help from TA on name= and changing from softmax to sigmoid)
department_output = layers.Dense(y_train_enc_department.shape[1], activation='sigmoid', name='department_output')(department_hidden)
# maybe softmax 

# Create the model
(help from Instructor on changing to a dictionary from a list)

# Train the Model and Evaluate the Model TA helped on using the correct values

# Print the Accuracy for both department and attrition
(TA helped me print the Eval results in order to print the "Department Accuracy" and "Attrition Accuracy" by showing me how to correctly add the index position)