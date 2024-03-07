# Part A: Unit Testing - Lists 📃
Let's say we have a simple function that calculates the average of a list of numbers. 
We want to perform unit testing on this function to make sure it works correctly. 
Here's the function and an example of how you might set up a test table:
````py
	# Function to calculate the average of a list of numbers
	def calculate_average(numbers):
	    if not numbers:
	        return None
	
	    total = 0
	    for num in numbers:
	        total += num
	
	    return total / len(numbers)
````

Now, let's set up a test table with different cases to check if the function behaves as expected:

![image](https://github.com/ross-bish/Coursework-Project/assets/83789503/a567d94e-20b5-42ed-ad17-bb8970f298dc)


Now, let's write some simple code to perform the unit tests based on this test table:

````py
	# Define test cases
	test_cases = [
	    ([1, 2, 3, 4, 5], 3.0),
	    ([], None),
	    ([2, 4, 6, 8], 5.0),
	    ([1, 3, 5, 7, 9], 5.0),
	    ([0], 0.0),
	]
	
	# Perform the tests
	for test_case in test_cases:
	    input_data = test_case[0]
	    expected_output = test_case[1]
	    
	    result = calculate_average(input_data)
	    
	    if result == expected_output:
	        status = "Pass"
	    else:
	        status = "Fail"
	    
	    print("Test - Input:", input_data, ", Expected:", expected_output, ", Result:", result, ", Status:", status)
````

In this example
	• We have a test table with different scenarios, and we run the calculate_average function with the provided inputs. 
	• We then check if the result matches the expected output and print the status of each test.

This is a basic example, and in real-world scenarios, you might use specialized testing libraries like unittest or pytest to organize and run your tests more efficiently.

### ⚔️Task - Experiment with the attached code and see if you can create a testing table of your own.


## Sample Code - 2
````py
# Function to calculate the average of a list of numbers
def calculate_average(numbers):
    if not numbers:
        return None

    total = 0
    for num in numbers:
        total += num

    return total / len(numbers)

# Test cases
test_cases = [
    ([1, 2, 3, 4, 5], 3.0),
    ([], None),
    ([2, 4, 6, 8], 5.0),
    ([1, 3, 5, 7, 9], 5.0),
    ([0], 0.0),
]

# Perform the tests
for i, (input_data, expected_output) in enumerate(test_cases, 1):
    result = calculate_average(input_data)
    status = "Pass" if result == expected_output else "Fail"
    print(f"Test {i}: {status} - Input: {input_data}, Expected: {expected_output}, Result: {result}")

````
### 💡Note: Let's explore how this final for loop works


1. `for i, (input_data, expected_output) in enumerate(test_cases, 1):`
   - This line is a `for` loop that iterates through each test case in the `test_cases` list.
   - `enumerate(test_cases, 1)` is used to loop through the `test_cases` list along with an index `i`. The `1` indicates the starting index.
   - `(input_data, expected_output)` is a tuple unpacking. It assigns the values of each test case to `input_data` and `expected_output`.

2. `result = calculate_average(input_data)`
   - This line calls the `calculate_average` function with the `input_data` from the current test case.
   - The result is stored in the variable `result`.

3. `status = "Pass" if result == expected_output else "Fail"`
   - This is a conditional (ternary) statement. It checks if the `result` is equal to the `expected_output`.
   - If they are equal, it assigns the string "Pass" to the variable `status`; otherwise, it assigns "Fail".

4. `print(f"Test {i}: {status} - Input: {input_data}, Expected: {expected_output}, Result: {result}")`
   - This line prints the result of the test.
   - It uses an f-string to format the output, displaying the test number (`i`), the status (`Pass` or `Fail`), the input data, the expected output, and the actual result.

So, in summary, this code runs a series of tests, calculates the result using the `calculate_average` function, compares it with the expected output, and prints the status of each test. The `enumerate` function is used to provide a test number (`i`) for better readability.



## Sample Code - 3
````py
# Function to calculate the average of a list of numbers
def calculate_average(numbers):
    if not numbers:
        return None  # To handle an empty list
    return sum(numbers) / len(numbers)

# Test cases
test_cases = [
    ([1, 2, 3, 4, 5], 3.0),
    ([], None),
    ([2, 4, 6, 8], 5.0),
    ([1, 3, 5, 7, 9], 5.0),
    ([0], 0.0),
]

# Perform the tests
for i, (input_data, expected_output) in enumerate(test_cases, 1):
    result = calculate_average(input_data)
    status = "Pass" if result == expected_output else "Fail"
    print(f"Test {i}: {status} - Input: {input_data}, Expected: {expected_output}, Result: {result}")

````

# Part B: Unit Testing - Login Page 👨🏽‍💻
Now let's create a simple example of a login page, a function to validate the User's login credentials, and a test table with various test cases. 

1. Firstly, here is the code for a basic login function:
 
````py
	# Function to validate login credentials
	def validate_login(username, password):
	    # In a real-world scenario, you'd check against a database or some secure storage
	    # For simplicity, let's consider a hardcoded username and password
	    valid_username = "student"
	    valid_password = "1234"
	
	    if username == valid_username and password == valid_password:
	        return True
	    else:
	        return False
````

2. Now, let's create a test table with different test cases:

````py
	# Test cases for login validation
	login_test_cases = [
	    ("student", "1234", True),  # Correct username and password, should pass
	    ("admin", "admin123", False),  # Incorrect username, should fail
	    ("student", "wrongpass", False),  # Incorrect password, should fail
	    ("user123", "pass123", False),  # Non-existent user, should fail
	    ("", "", False),  # Empty username and password, should fail
	]

````

3. Now, let's perform the tests:

````py
	# Perform the login tests
	for i in range(len(login_test_cases)):
	    test_case = login_test_cases[i]
	    username = test_case[0]
	    password = test_case[1]
	    expected_result = test_case[2]
	
	    result = validate_login(username, password)
	
	    if result == expected_result:
	        status = "Pass"
	    else:
	        status = "Fail"
	
	    print("Login Test {}: {} - Username: {}, Password: {}, Expected: {}, Result: {}".format(i + 1, status, username, password, expected_result, result))
````

### 💡Note: In this example

- The ``validate_login`` function checks if the provided username and password match a hardcoded valid combination.
- The ``login_test_cases`` list contains different scenarios, including correct and incorrect username/password combinations.
- The loop goes through each test case, runs the  ``validate_login`` function, compares the result with the expected outcome, and prints the status of each test.

Feel free to customize the test cases or the  validate_login function based on the specific requirements of your Coursework project.



## Sample Code - 2
````py
# Function to validate login credentials
def validate_login(username, password):
    # In a real-world scenario, you'd check against a database or some secure storage
    # For simplicity, let's consider a hardcoded username and password
    valid_username = "student"
    valid_password = "1234"

    if username == valid_username and password == valid_password:
        return True
    else:
        return False


# Test cases for login validation
login_test_cases = [
    ("student", "1234", True),  # Correct username and password, should pass
    ("admin", "admin123", False),  # Incorrect username, should fail
    ("student", "wrongpass", False),  # Incorrect password, should fail
    ("user123", "pass123", False),  # Non-existent user, should fail
    ("", "", False),  # Empty username and password, should fail
]


# Perform the login tests
for i, (username, password, expected_result) in enumerate(login_test_cases, 1):
    result = validate_login(username, password)
    status = "Pass" if result == expected_result else "Fail"
    print(f"Login Test {i}: {status} - Username: {username}, Password: {password}, Expected: {expected_result}, Result: {result}")

````

