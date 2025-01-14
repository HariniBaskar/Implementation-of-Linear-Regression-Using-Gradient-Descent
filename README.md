# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required Packages and read the .csv file
2. Define a function named ComputeCost and compute the output
3. Define a function named gradientDescent and iterate the loop
4. Predict the required graphs using scatterplots.
## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Harini.B
RegisterNumber:  212221230035
*/
```
```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("ex1.txt",header=None)

plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(5,30,step=5))
plt.xlabel("Population of City (10,000s")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def computeCost(x,y,theta):
  """
  Take in a numpy array x, y, theta and generate the cost function ina linear regression model
  """
  m=len(y) #length of the training data
  h=x.dot(theta) #hypothesis
  square_err=(h - y)**2
  return 1/(2*m) * np.sum(square_err) #returning J 
  
data_n=data.values
m=data_n[:,0].size
x=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))

computeCost(x,y,theta) #call the function

def gradientDescent(x,y,theta,alpha,num_iters):
  """
  Take in numpy array x, y and theta and update theta by taking num_iters with learning rate of alpha
  return theta and the list of the cost of theta during each iteration
  """
  m=len(y)
  J_history=[]
  for i in range(num_iters):
    predictions=x.dot(theta)
    error=np.dot(x.transpose(),(predictions-y))
    descent=alpha*1/m*error
    theta-=descent
    J_history.append(computeCost(x,y,theta))
  return theta, J_history

theta,J_history  =gradientDescent(x,y,theta,0.01,1500)
print("h(x) = "+str(round(theta[0,0],2))+"+"+str(round(theta[1,0],2))+"x1")

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Gradient Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="red")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")

def predict(x,theta):
    #takes in numpy array of x and theta and return the predicted value of y based on theta
    predictions=np.dot(theta.transpose(),x)
    return predictions[0]
    
predict1=predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000, we predict a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("For population = 70,000, we predict a profit of $"+str(round(predict2,0)))
```

## Output:

## PROFIT PREDICTION GRAPH
![ml31](https://user-images.githubusercontent.com/93427253/229272967-472263f8-7706-45ec-81ec-26a05dcb1430.png)

## ComputeCost OUTPUT
![ml32](https://user-images.githubusercontent.com/93427253/229272974-e6c49750-126e-46e5-a5fc-a4d9f994358b.png)

## gradientDescent OUTPUT
![ml33](https://user-images.githubusercontent.com/93427253/229273000-bb490bbc-70a6-4b55-b141-2b2ae2f05524.png)

## COST FUNCTION USING GRADIENT DESCENT
![ml34](https://user-images.githubusercontent.com/93427253/229273022-3253db22-c366-4316-8607-69bc6609fa81.png)

## PROFIT PREDICTION GRAPH
![ml35](https://user-images.githubusercontent.com/93427253/229273028-04ef238a-a341-47bd-81fd-4e53a9453079.png)

## POPULATION PREDICTION
![ml36](https://user-images.githubusercontent.com/93427253/229273040-9f013b17-850a-47f4-add9-9d93938a5098.png)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
