# BrowserFamily_Version_Extractor
The goal of the task is to build a tool to extract browser familiy and major version from user agents. 

# Research
Standard User-Agent Format:
The User-Agent request-header field contains information about the user agent originating the request. This is for statistical purposes, the tracing of protocol violations, and automated recognition of user agents for the sake of tailoring responses to avoid particular user agent limitations. User agents SHOULD include this field with requests. The field can contain multiple product tokens (section 3.8) and comments identifying the agent and any subproducts which form a significant part of the user agent. 

# Machine Learning Model
I choose the sklearn-decision-tree. Because this obviously is a classification question. Decision Tree is a non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features. After observing the training dataset and question paper, I am trying to build feature-set based on the browser-family categories. For example, I got that there is a unique feature for Facebook browser in User-Agent format, it's the FB* properties, like [FB_IAB/FB4A;FBAV/106.0.0.26.68;] and etc.For other browser family, there are other features. I built a 25-features vector for each line of input X, and extract the output Y from the data-coding-exercise.txt. Then put in the sklearn-decision-tree api to genereate my own model. Also, when the model predict the browser-family based on test-dataset, we can find the version in the User-Agent format according to its matching model.

# Run Instructions:
For generalizability and scalability, I run it in virtual envinroment and install consistent lib.
1. virtualenv .
2. source ./bin/activate
3. pip install -r requirements.txt
4. python run.py data_coding_exercise.txt test_data_coding_exercise.txt output_data.txt

# Compare with test_data_coding_exercise.txt
I add some test-cases in the test file. Temporay accuracy is 100%.
