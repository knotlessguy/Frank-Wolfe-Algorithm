# Frank-Wolfe-Algorithm
Implementation of the Frank Wolfe Algorithm for transportation network analysis

# Import scipy.integrate as integrate (Function used in code)

The quad function is a function from an old Fortran library. It works by judging by the flatness and slope of the function it is integrating how to treat the step size it uses for numerical integration in order to maximize efficiency. What this means is that you may get slightly different answers from one region to the next even if they're analytically the same.


# Minimizing a linear objective function (Linear Programming)

scipy.optimize.linprog
scipy.optimize.linprog(c, A_ub=None, b_ub=None, A_eq=None, b_eq=None, bounds=None, method='simplex', callback=None, options=None)[source]
Minimize a linear objective function subject to linear equality and inequality constraints.

Linear Programming is intended to solve the following problem form:

Minimize:     c^T * x

Subject to:   A_ub * x <= b_ub
              A_eq * x == b_eq

# Main functions
#### Step 1: Network Representation and Data Structure
## Define the link-node matrix

LinkNode = pd.read_csv("linknode2.csv", header = None)  #Reading it as a dataframe <br>
LinkNode = LinkNode.as_matrix()


## Import Demand matrix (Q)
Q = pd.read_csv("demand.csv", header = None) #Q to demand <br>
Q = Q.as_matrix()

## create travel time vector (ta)
n = 76 # number of total links (Using sample values, to be varied according to our input) <br>
k = 24 # number of total nodes (Using sample values, to be varied according to our input) <br>

## Create link flow matrix for iterations (Y)
s = (n,k) # 76 links, 24 nodes/origins <br>
#Y = np.zeros(s) # each entry represents the flow on link a from origin i

## Import the travel time coeff. estimation matrix (Coeff)
coeff = pd.read_csv("coefficient2.csv", header = None) <br>
coeff = coeff.as_matrix() #Converting it to matrix form 

### Step 2: Shortest Path Searching (Solve LP)

##Initialization

t0 = coeff [:,0] # free flow travel time from 1st column of *Coeff* <br>
ca = coeff[:,1] # capacity for each link <br>

# Meaning of norm used as a criteria in while loop

The Frobenius norm is given by :

 ||A||_F = [\sum_{i,j} abs(a_{i,j})^2]^{1/2} <br>
The nuclear norm is the sum of the singular values.

For more information check the project report
