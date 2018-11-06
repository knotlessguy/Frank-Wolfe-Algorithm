# Frank-Wolfe-Algorithm
Implementation of the Frank Wolfe Algorithm for transportation network analysis

# import scipy.integrate as integrate

The quad function is a function from an old Fortran library. It works by judging by the flatness and slope of the function it is integrating how to treat the step size it uses for numerical integration in order to maximize efficiency. What this means is that you may get slightly different answers from one region to the next even if they're analytically the same.

![Test](https://raw.githubusercontent.com/knotlessguy/Frank-Wolfe-Algorithm/tree/master/images/img1.PNG)

<img src='https://raw.githubusercontent.com/knotlessguy/Frank-Wolfe-Algorithm/tree/master/images/img1.PNG'/>

# Minimizing a linear objective function (Linear Programming)

scipy.optimize.linprog
scipy.optimize.linprog(c, A_ub=None, b_ub=None, A_eq=None, b_eq=None, bounds=None, method='simplex', callback=None, options=None)[source]
Minimize a linear objective function subject to linear equality and inequality constraints.

Linear Programming is intended to solve the following problem form:

Minimize:     c^T * x

Subject to:   A_ub * x <= b_ub
              A_eq * x == b_eq

# main functions
#### Step 1: Network Representation and Data Structure
## Define the link-node matrix

LinkNode = pd.read_csv("linknode2.csv", header = None)  #Reading it as a dataframe <br>
LinkNode = LinkNode.as_matrix()


## Import Demand matrix (Q)
Q = pd.read_csv("demand.csv", header = None) #Q to demand <br>
Q = Q.as_matrix()
