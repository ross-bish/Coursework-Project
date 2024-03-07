# Linear Regression
![image](https://github.com/ross-bish/Coursework-Project/assets/83789503/523b47ec-03a5-4662-b3fa-b87bc8fd28e2)

What is Linear Regression?

Imagine you have a bunch of data points (like dots on a graph), and you notice that they seem to form a straight line when you connect them. Linear regression is a way to find and understand that line mathematically. In simpler terms, it helps you figure out the relationship between two things.

## Example 1:

Let's say you have data about the number of hours you spend studying and the grades you get. 
You might notice that the more you study, the higher your grades tend to be. 
Linear regression can help you create a formula (equation of a line) to predict your grades based on the number of hours you study.

How does it work?
	• The goal is to find the best-fitting line that minimizes the difference between the predicted values (what the line says) and the actual values in your data.

Applying Linear Regression in Python - In Python, there are libraries like ``scikit-learn`` that make it easy to use linear regression. 

### Here's a simple example:

````py
# Importing necessary libraries
from sklearn.linear_model import LinearRegression
import numpy as np

# Creating some example data
hours_studied = np.array([1, 2, 3, 4, 5])  # X (independent variable)
grades = np.array([60, 70, 80, 90, 100])    # Y (dependent variable)

# Reshape the data to make it work with scikit-learn
X = hours_studied.reshape(-1, 1)

# Creating a linear regression model
model = LinearRegression()

# Training the model (fitting the line to the data)
model.fit(X, grades)

# Making predictions
predicted_grades = model.predict(X)

# Print the slope and intercept of the line
print("Slope (m):", model.coef_[0])
print("Intercept (c):", model.intercept_)
````

In this example, ``hours_studied`` is our X (independent variable), and ``grades`` is our Y (dependent variable). 
The model is trained on this data, and then you can use it to make predictions.

Try to type up the following code and see what output you receive.

After running this code, you'll get the equation of the line (your linear model) in the form of ``y = mx +c``, where `m` is the slope and `c` is the intercept.

This equation represents the relationship between the hours studied (X) and the predicted grades (Y) based on the data you provided.



### Example 2:
Now let's try to understand our output.
The output you received provides the parameters of the linear regression model:

``Slope (m): 10.0``
- This means that for every one-unit increase in the hours studied (X), the predicted grades (Y) will increase by 10 units. In simpler terms, it suggests that studying for one additional hour is associated with an increase of 10 points in the predicted grades.

``Intercept (c): 50.0``
- The intercept represents the predicted value of Y when X is 0. In this case, it suggests that if someone studied for zero hours, the predicted grade would be 50.0. However, in practical terms, this intercept might not have a meaningful interpretation, as it's unlikely for a student to score 50 without studying.

So, the equation of your linear model is approximately:  ``Predicted Grades =(10 x Hours Studied)+ 50``

This equation describes the best-fitting line through your data points based on the linear regression model you trained. You can use this equation to predict grades for any given number of hours studied.

### Question to make you think 🤔 
• But if 100% is the max grade I can get, this formula (model) doesn't work?

To account for the maximum grade being 100, you can impose a constraint on your model to ensure that the predicted grades never exceed this maximum value. One simple way to do this is by setting a maximum limit on the predicted grades.

Here's how you can modify your code to incorporate this constraint:

````py
# Importing necessary libraries
from sklearn.linear_model import LinearRegression
import numpy as np

# Creating some example data
hours_studied = np.array([1, 2, 3, 4, 5])  # X (independent variable)
grades = np.array([60, 70, 80, 90, 100])    # Y (dependent variable)

# Reshape the data to make it work with scikit-learn
X = hours_studied.reshape(-1, 1)

# Creating a linear regression model
model = LinearRegression()

# Training the model (fitting the line to the data)
model.fit(X, grades)

# Making predictions
predicted_grades = model.predict(X)

# Applying a constraint to the predicted grades
predicted_grades = np.minimum(predicted_grades, 100)  # Set maximum grade to 100

# Print the slope and intercept of the line
print("Slope (m):", model.coef_[0])
print("Intercept (c):", model.intercept_)

# Print the predicted grades
print("Predicted Grades:", predicted_grades)
````

In this modified program, after making predictions using the linear regression model, we apply a constraint using the ``np.minimum()`` function to ensure that the predicted grades do not exceed 100. This ensures that the model respects the maximum grade limit.

Now, when you run the code, the predicted grades will never go above 100, even if the model predicts higher values based on the linear relationship between hours studied and grades.


### Question to make you think 🤔 
What does this line of code do?

````py
# Reshape the data to make it work with scikit-learn
X = hours_studied.reshape(-1, 1)
````

Answer:
This line is used to reshape the ``hours_studied`` array. This is necessary because scikit-learn's Linear Regression model expects the input features (`X`) to be a 2D array or matrix, and hours_studied is initially a 1D array.

Breaking it down…

- ``hours_studied`` is initially a 1D array like ``[1, 2, 3, 4, 5]``.
- The ``reshape(-1, 1)`` method is applied to change the shape of the array. The ``-1`` in the reshape function is a placeholder that means "whatever is needed". The ``1`` indicates that you want each inner array to have one element.
- After reshaping, X becomes a 2D array or matrix, for example: ``[[1], [2], [3], [4], [5]]``.

In the context of linear regression, it's common for the input features (X) to be a 2D array, even if you only have one feature (in this case, ``hours_studied``). 
This ensures compatibility with scikit-learn's requirements, which expect a 2D array for the input features.


## Part B: Visualisation 📈
To visualize your linear regression model on a graph, you can use a plotting library like ``matplotlib``. 
Here's an example of how you can plot your data points and the regression line:

````py
import matplotlib.pyplot as plt

# Scatter plot of the actual data
plt.scatter(hours_studied, grades, color='blue', label='Actual Data')

# Plotting the regression line
plt.plot(hours_studied, predicted_grades, color='red', label='Regression Line')

# Adding labels and title
plt.xlabel('Hours Studied')
plt.ylabel('Grades')
plt.title('Linear Regression Model')
plt.legend()  # Display legend to distinguish actual data and regression line

# Show the plot
plt.show()
````

This code uses ``plt.scatter()`` to plot your actual data points as blue dots and ``plt.plot()`` to draw the regression line in red. 
The legend helps differentiate between the actual data and the regression line.

Update your existing program with this code, it should generate a plot displaying your data points and the linear regression line as shown below.

![image](https://github.com/ross-bish/Coursework-Project/assets/83789503/003ab5ad-1d2f-4354-8a28-da3c7001cb5d)

