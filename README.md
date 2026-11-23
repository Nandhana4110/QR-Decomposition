# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Nandhana Marien F
RegisterNumber: 26015782
'''
import os
os.environ["OPENBLAS_NUM_THREADS"] = "1"
import numpy as np

def QR_Decomposition(A):
    A = np.array(A, dtype=float)
    m,n = A.shape
    
    Q = np.zeros((m,n))
    R = np.zeros((n,n))
    
    for j in range(n):
        v = A[:,j]
        for i in range(j):
            R[i,j] = np.dot(Q[:,i],A[:,j])
            v = v-R[i,j]*Q[:,i]
            
        R[j,j] = np.linalg.norm(v)
        Q[:,j] = v/R[j,j]
    return Q,R  
    
A = np.array(eval(input()))
Q,R=QR_Decomposition(A)

print("The Q Matrix is \n",Q)
print("The R Matrix is \n",R)
```

## Output
<img width="756" height="882" alt="image" src="https://github.com/user-attachments/assets/0ea3ea3c-54cd-4b81-b0b7-d58079fecfa2" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
