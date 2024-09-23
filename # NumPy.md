## <center>NumPy</center>

### Useful Links

[Python Quick Reference](https://www.python.org/ftp/python/doc/1.1/quick-ref.1.1.html)

[Python3 cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)

[Python.org](https://www.python.org/)

[Python Standard Library](https://docs.python.org/3/library/index.html)

[Python Functions](https://docs.python.org/3/library/functions)

[Python NumPy](https://numpy.org/)

[Matplotlib (PyPlot)](https://matplotlib.org/stable/index.html#)

---

|<td colspan=3> <center><bold><h3>**Table of contents**<center>|||
|---|:---|:---:|
|**01.**|[**NumPy**](#NumPy;)|import library,<br>cast list to numpy,<br>numpy matrix objects,<br>largest element in array or matrix,<br>zeros( ), ones( ), eye( ), empty( ) functions,<br>cast dataset to ndarray<br>index / slice arrays,<br>dtype / size / ndim / shape methods,<br>array addition / subtraction / multiplication,<br>add axis to array<br>hadamard / dot product,<br>matrix multiplication,<br>norm of a matrix or vector,<br>transpose a matrix,<br>trace of a matrix,<br>determinant of a matrix,<br>inverse of a matrix,<br>Moore-Penrose pseudoinverse,<br>eig function (eigenvalues/vectors),<br>min, max, square root, mean, standard deviation of an array, pi,<br>random numbers with Numpy, int / float / seed<br>random binomial / uniform / poisson / normal / gassian distributions<br>linspace,<br>matplotlib|

* NumPy is a Python library for data analysis, mainly used for numerical data  
* Can be computationally faster and require less memory than regular Python  

**import numpy**:  

**`import numpy as np`**  

* Keyword **"import"** to import library  
* **"numpy"** is the library name  
* Keyword **"as"** is **optional** to change name referred to in script...in this case to the standard abbreviation "np"  
* Once the library has been imported, we have access to pre-built functions and classes  


```python
# importing numpy library and assigning it to "np"

import numpy as np
```

**import specific package**  

**`from libraryName import packageName`**  
* Will import only the package named from the library named  
* Can change name package will be referred to in script by optionally including **as newReferringName** after imported package name  

**cast list to numpy n-dimensional (nd) array**:  

**`np_var = np.array([ele1, ele2...])`**  
* An array is a list that is arranged in **multiple directions**, see picture below  
* When there are more dimensions there will be more nested lists, note Python will print out as a table for easier viewing  
* Assign to a variable to save  
* "np" is the library name as imported  *
* Requires **round AND square** brackets  
* NumPy **array elements** need to be the **SAME type**  
* The main **difference between np.array** and **np.asarray** is that np.array creates a copy of the object array and does not reflect changes to the original array. np.asarray reflects changes to the original array  

![](http://venus.ifca.unican.es/Rintro/_images/dataStructuresNew.png "visualization of Vectors, Matrices and Arrays")


```python
# example casting list to nd array

A = np.array([1,3,5,6])
print(A)
print(type(A))
```

    [1 3 5 6]
    <class 'numpy.ndarray'>
    

**numpy matrix object:**  

**`np_var = np.matrix([[ele11,ele12...],`**  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**`[ele21, ele22...]])`**  
* Returns a matrix from an array-like object, or from a string of data  
* A matrix is a specialized 2-D array that retains its 2-D nature through operations  
* It has certain special operators, such as `*` (matrix multiplication) and `**` (matrix power)  


```python
A = np.matrix([[1,2],
             [3,4]])

print(A)
```

    [[1 2]
     [3 4]]
    

**largest element in an array or matrix:**  

**`np.max(np_var)`**  
* Returns the largest element in array or matrix  


```python
A = np.matrix([[12,13],
               [9,2]])
np.max(A)
```




    13



**zeros**:  

**`np.zeros(shape)`**  
* Creates an array of given shape **filled with zeros**  
* **`shape`** is the number of elements in each direction in the array, **1D arrays** need just the **number of elements**, **2D arrays** should be given as a **tuple** (10,3) would produce an array with 10 rows, each with 3 elements  
* Note the zeros will be entered as **floats**  
* **If you don't have the data**, best practice is to initialise a matrix with zeros and populate it


```python
# Creats a 1D array full of zeros

np.zeros(5).ndim
```




    1




```python
# Creates a 2D array full of zeros

np.zeros((10,3))
```




    array([[0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.]])



**ones**:  

**`np.ones(shape)`**  
* Similar to zeros (above), but fills the array with ones  
* Note the ones are entered as **floats**  


```python
# Creates a 2D array full of ones

np.ones((3,4))
```




    array([[1., 1., 1., 1.],
           [1., 1., 1., 1.],
           [1., 1., 1., 1.]])



**eye** function (**Identity matrix**):  

**`np.eye(N, M=None)`**  
* **`N`** is the number of **rows** in the output  
* **`M`** is the number of **columns**, defaults to **`N`** when set to **None**  
* Produces a matrix filled with **zeros**, with **ones on the diagonal**  
* If **`M`** is not specified, produces a **square matrix** (same number of rows and columns)  
* Matrices of this form (max one '1' per row and column) are called permutation matrices  


```python
np.eye(5)
```




    array([[1., 0., 0., 0., 0.],
           [0., 1., 0., 0., 0.],
           [0., 0., 1., 0., 0.],
           [0., 0., 0., 1., 0.],
           [0., 0., 0., 0., 1.]])



**empty** function:  

**`np.empty(shape, dtype=float)`**  
* **`dtype`** Desired output data-type for the array, e.g, numpy.int8. Default is numpy.float64  
* Use **`dtype='U10'`** for **unicode string of max length 10**  


```python
# creating an empty array
emptyArray = np.empty(5, dtype='U10')
print(emptyArray)
```

    ['' '' '' '' '']
    

**Cast dataset (list) as ndarray**:  

**`ndarrayVar = np.asarray(dataset)`**  
* Casts **`dataset`** as ndarray  
* The main **difference between np.array** and **np.asarray** is that np.array creates a copy of the object array and does not reflect changes to the original array. np.asarray reflects changes to the original array  


```python
# Reads in csv file, adds data to a dataset (list) 
# Then adds data into its own dataset and labels into another dataset in preperation for casting to an ndarray

import csv
import pandas as pd

dataset =[]

with open('data/iris.csv') as fs:
    csv_reader = csv.reader(fs)
    header = next(csv_reader)
    for r in csv_reader:
        dataset.append(r)

X = [None] * len(dataset)    # Data
Y = [None] * len(dataset)    # Labels

for i in range(len(dataset)):
    X[i] = [ float(x) for x in dataset[i][0:-1]]
    Y[i] = dataset[i][-1]
    
del dataset

print("\nX:")
print(X)
print("\nY:")
print(Y)
```

    
    X:
    [[5.1, 3.5, 1.4, 0.2], [4.9, 3.0, 1.4, 0.2], [4.7, 3.2, 1.3, 0.2], [4.6, 3.1, 1.5, 0.2], [5.0, 3.6, 1.4, 0.2], [5.4, 3.9, 1.7, 0.4], [4.6, 3.4, 1.4, 0.3], [5.0, 3.4, 1.5, 0.2], [4.4, 2.9, 1.4, 0.2], [4.9, 3.1, 1.5, 0.1], [5.4, 3.7, 1.5, 0.2], [4.8, 3.4, 1.6, 0.2], [4.8, 3.0, 1.4, 0.1], [4.3, 3.0, 1.1, 0.1], [5.8, 4.0, 1.2, 0.2], [5.7, 4.4, 1.5, 0.4], [5.4, 3.9, 1.3, 0.4], [5.1, 3.5, 1.4, 0.3], [5.7, 3.8, 1.7, 0.3], [5.1, 3.8, 1.5, 0.3], [5.4, 3.4, 1.7, 0.2], [5.1, 3.7, 1.5, 0.4], [4.6, 3.6, 1.0, 0.2], [5.1, 3.3, 1.7, 0.5], [4.8, 3.4, 1.9, 0.2], [5.0, 3.0, 1.6, 0.2], [5.0, 3.4, 1.6, 0.4], [5.2, 3.5, 1.5, 0.2], [5.2, 3.4, 1.4, 0.2], [4.7, 3.2, 1.6, 0.2], [4.8, 3.1, 1.6, 0.2], [5.4, 3.4, 1.5, 0.4], [5.2, 4.1, 1.5, 0.1], [5.5, 4.2, 1.4, 0.2], [4.9, 3.1, 1.5, 0.1], [5.0, 3.2, 1.2, 0.2], [5.5, 3.5, 1.3, 0.2], [4.9, 3.1, 1.5, 0.1], [4.4, 3.0, 1.3, 0.2], [5.1, 3.4, 1.5, 0.2], [5.0, 3.5, 1.3, 0.3], [4.5, 2.3, 1.3, 0.3], [4.4, 3.2, 1.3, 0.2], [5.0, 3.5, 1.6, 0.6], [5.1, 3.8, 1.9, 0.4], [4.8, 3.0, 1.4, 0.3], [5.1, 3.8, 1.6, 0.2], [4.6, 3.2, 1.4, 0.2], [5.3, 3.7, 1.5, 0.2], [5.0, 3.3, 1.4, 0.2], [7.0, 3.2, 4.7, 1.4], [6.4, 3.2, 4.5, 1.5], [6.9, 3.1, 4.9, 1.5], [5.5, 2.3, 4.0, 1.3], [6.5, 2.8, 4.6, 1.5], [5.7, 2.8, 4.5, 1.3], [6.3, 3.3, 4.7, 1.6], [4.9, 2.4, 3.3, 1.0], [6.6, 2.9, 4.6, 1.3], [5.2, 2.7, 3.9, 1.4], [5.0, 2.0, 3.5, 1.0], [5.9, 3.0, 4.2, 1.5], [6.0, 2.2, 4.0, 1.0], [6.1, 2.9, 4.7, 1.4], [5.6, 2.9, 3.6, 1.3], [6.7, 3.1, 4.4, 1.4], [5.6, 3.0, 4.5, 1.5], [5.8, 2.7, 4.1, 1.0], [6.2, 2.2, 4.5, 1.5], [5.6, 2.5, 3.9, 1.1], [5.9, 3.2, 4.8, 1.8], [6.1, 2.8, 4.0, 1.3], [6.3, 2.5, 4.9, 1.5], [6.1, 2.8, 4.7, 1.2], [6.4, 2.9, 4.3, 1.3], [6.6, 3.0, 4.4, 1.4], [6.8, 2.8, 4.8, 1.4], [6.7, 3.0, 5.0, 1.7], [6.0, 2.9, 4.5, 1.5], [5.7, 2.6, 3.5, 1.0], [5.5, 2.4, 3.8, 1.1], [5.5, 2.4, 3.7, 1.0], [5.8, 2.7, 3.9, 1.2], [6.0, 2.7, 5.1, 1.6], [5.4, 3.0, 4.5, 1.5], [6.0, 3.4, 4.5, 1.6], [6.7, 3.1, 4.7, 1.5], [6.3, 2.3, 4.4, 1.3], [5.6, 3.0, 4.1, 1.3], [5.5, 2.5, 4.0, 1.3], [5.5, 2.6, 4.4, 1.2], [6.1, 3.0, 4.6, 1.4], [5.8, 2.6, 4.0, 1.2], [5.0, 2.3, 3.3, 1.0], [5.6, 2.7, 4.2, 1.3], [5.7, 3.0, 4.2, 1.2], [5.7, 2.9, 4.2, 1.3], [6.2, 2.9, 4.3, 1.3], [5.1, 2.5, 3.0, 1.1], [5.7, 2.8, 4.1, 1.3], [6.3, 3.3, 6.0, 2.5], [5.8, 2.7, 5.1, 1.9], [7.1, 3.0, 5.9, 2.1], [6.3, 2.9, 5.6, 1.8], [6.5, 3.0, 5.8, 2.2], [7.6, 3.0, 6.6, 2.1], [4.9, 2.5, 4.5, 1.7], [7.3, 2.9, 6.3, 1.8], [6.7, 2.5, 5.8, 1.8], [7.2, 3.6, 6.1, 2.5], [6.5, 3.2, 5.1, 2.0], [6.4, 2.7, 5.3, 1.9], [6.8, 3.0, 5.5, 2.1], [5.7, 2.5, 5.0, 2.0], [5.8, 2.8, 5.1, 2.4], [6.4, 3.2, 5.3, 2.3], [6.5, 3.0, 5.5, 1.8], [7.7, 3.8, 6.7, 2.2], [7.7, 2.6, 6.9, 2.3], [6.0, 2.2, 5.0, 1.5], [6.9, 3.2, 5.7, 2.3], [5.6, 2.8, 4.9, 2.0], [7.7, 2.8, 6.7, 2.0], [6.3, 2.7, 4.9, 1.8], [6.7, 3.3, 5.7, 2.1], [7.2, 3.2, 6.0, 1.8], [6.2, 2.8, 4.8, 1.8], [6.1, 3.0, 4.9, 1.8], [6.4, 2.8, 5.6, 2.1], [7.2, 3.0, 5.8, 1.6], [7.4, 2.8, 6.1, 1.9], [7.9, 3.8, 6.4, 2.0], [6.4, 2.8, 5.6, 2.2], [6.3, 2.8, 5.1, 1.5], [6.1, 2.6, 5.6, 1.4], [7.7, 3.0, 6.1, 2.3], [6.3, 3.4, 5.6, 2.4], [6.4, 3.1, 5.5, 1.8], [6.0, 3.0, 4.8, 1.8], [6.9, 3.1, 5.4, 2.1], [6.7, 3.1, 5.6, 2.4], [6.9, 3.1, 5.1, 2.3], [5.8, 2.7, 5.1, 1.9], [6.8, 3.2, 5.9, 2.3], [6.7, 3.3, 5.7, 2.5], [6.7, 3.0, 5.2, 2.3], [6.3, 2.5, 5.0, 1.9], [6.5, 3.0, 5.2, 2.0], [6.2, 3.4, 5.4, 2.3], [5.9, 3.0, 5.1, 1.8]]
    
    Y:
    ['setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'setosa', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'versicolor', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica', 'virginica']
    


```python
# Casts data dataset to nparray "Xnp" and labels dataset to nparray "Ynp"

Xnp = np.asarray(X)
Ynp = np.asarray(Y)

print(Xnp)
```

    [[5.1 3.5 1.4 0.2]
     [4.9 3.  1.4 0.2]
     [4.7 3.2 1.3 0.2]
     [4.6 3.1 1.5 0.2]
     [5.  3.6 1.4 0.2]
     [5.4 3.9 1.7 0.4]
     [4.6 3.4 1.4 0.3]
     [5.  3.4 1.5 0.2]
     [4.4 2.9 1.4 0.2]
     [4.9 3.1 1.5 0.1]
     [5.4 3.7 1.5 0.2]
     [4.8 3.4 1.6 0.2]
     [4.8 3.  1.4 0.1]
     [4.3 3.  1.1 0.1]
     [5.8 4.  1.2 0.2]
     [5.7 4.4 1.5 0.4]
     [5.4 3.9 1.3 0.4]
     [5.1 3.5 1.4 0.3]
     [5.7 3.8 1.7 0.3]
     [5.1 3.8 1.5 0.3]
     [5.4 3.4 1.7 0.2]
     [5.1 3.7 1.5 0.4]
     [4.6 3.6 1.  0.2]
     [5.1 3.3 1.7 0.5]
     [4.8 3.4 1.9 0.2]
     [5.  3.  1.6 0.2]
     [5.  3.4 1.6 0.4]
     [5.2 3.5 1.5 0.2]
     [5.2 3.4 1.4 0.2]
     [4.7 3.2 1.6 0.2]
     [4.8 3.1 1.6 0.2]
     [5.4 3.4 1.5 0.4]
     [5.2 4.1 1.5 0.1]
     [5.5 4.2 1.4 0.2]
     [4.9 3.1 1.5 0.1]
     [5.  3.2 1.2 0.2]
     [5.5 3.5 1.3 0.2]
     [4.9 3.1 1.5 0.1]
     [4.4 3.  1.3 0.2]
     [5.1 3.4 1.5 0.2]
     [5.  3.5 1.3 0.3]
     [4.5 2.3 1.3 0.3]
     [4.4 3.2 1.3 0.2]
     [5.  3.5 1.6 0.6]
     [5.1 3.8 1.9 0.4]
     [4.8 3.  1.4 0.3]
     [5.1 3.8 1.6 0.2]
     [4.6 3.2 1.4 0.2]
     [5.3 3.7 1.5 0.2]
     [5.  3.3 1.4 0.2]
     [7.  3.2 4.7 1.4]
     [6.4 3.2 4.5 1.5]
     [6.9 3.1 4.9 1.5]
     [5.5 2.3 4.  1.3]
     [6.5 2.8 4.6 1.5]
     [5.7 2.8 4.5 1.3]
     [6.3 3.3 4.7 1.6]
     [4.9 2.4 3.3 1. ]
     [6.6 2.9 4.6 1.3]
     [5.2 2.7 3.9 1.4]
     [5.  2.  3.5 1. ]
     [5.9 3.  4.2 1.5]
     [6.  2.2 4.  1. ]
     [6.1 2.9 4.7 1.4]
     [5.6 2.9 3.6 1.3]
     [6.7 3.1 4.4 1.4]
     [5.6 3.  4.5 1.5]
     [5.8 2.7 4.1 1. ]
     [6.2 2.2 4.5 1.5]
     [5.6 2.5 3.9 1.1]
     [5.9 3.2 4.8 1.8]
     [6.1 2.8 4.  1.3]
     [6.3 2.5 4.9 1.5]
     [6.1 2.8 4.7 1.2]
     [6.4 2.9 4.3 1.3]
     [6.6 3.  4.4 1.4]
     [6.8 2.8 4.8 1.4]
     [6.7 3.  5.  1.7]
     [6.  2.9 4.5 1.5]
     [5.7 2.6 3.5 1. ]
     [5.5 2.4 3.8 1.1]
     [5.5 2.4 3.7 1. ]
     [5.8 2.7 3.9 1.2]
     [6.  2.7 5.1 1.6]
     [5.4 3.  4.5 1.5]
     [6.  3.4 4.5 1.6]
     [6.7 3.1 4.7 1.5]
     [6.3 2.3 4.4 1.3]
     [5.6 3.  4.1 1.3]
     [5.5 2.5 4.  1.3]
     [5.5 2.6 4.4 1.2]
     [6.1 3.  4.6 1.4]
     [5.8 2.6 4.  1.2]
     [5.  2.3 3.3 1. ]
     [5.6 2.7 4.2 1.3]
     [5.7 3.  4.2 1.2]
     [5.7 2.9 4.2 1.3]
     [6.2 2.9 4.3 1.3]
     [5.1 2.5 3.  1.1]
     [5.7 2.8 4.1 1.3]
     [6.3 3.3 6.  2.5]
     [5.8 2.7 5.1 1.9]
     [7.1 3.  5.9 2.1]
     [6.3 2.9 5.6 1.8]
     [6.5 3.  5.8 2.2]
     [7.6 3.  6.6 2.1]
     [4.9 2.5 4.5 1.7]
     [7.3 2.9 6.3 1.8]
     [6.7 2.5 5.8 1.8]
     [7.2 3.6 6.1 2.5]
     [6.5 3.2 5.1 2. ]
     [6.4 2.7 5.3 1.9]
     [6.8 3.  5.5 2.1]
     [5.7 2.5 5.  2. ]
     [5.8 2.8 5.1 2.4]
     [6.4 3.2 5.3 2.3]
     [6.5 3.  5.5 1.8]
     [7.7 3.8 6.7 2.2]
     [7.7 2.6 6.9 2.3]
     [6.  2.2 5.  1.5]
     [6.9 3.2 5.7 2.3]
     [5.6 2.8 4.9 2. ]
     [7.7 2.8 6.7 2. ]
     [6.3 2.7 4.9 1.8]
     [6.7 3.3 5.7 2.1]
     [7.2 3.2 6.  1.8]
     [6.2 2.8 4.8 1.8]
     [6.1 3.  4.9 1.8]
     [6.4 2.8 5.6 2.1]
     [7.2 3.  5.8 1.6]
     [7.4 2.8 6.1 1.9]
     [7.9 3.8 6.4 2. ]
     [6.4 2.8 5.6 2.2]
     [6.3 2.8 5.1 1.5]
     [6.1 2.6 5.6 1.4]
     [7.7 3.  6.1 2.3]
     [6.3 3.4 5.6 2.4]
     [6.4 3.1 5.5 1.8]
     [6.  3.  4.8 1.8]
     [6.9 3.1 5.4 2.1]
     [6.7 3.1 5.6 2.4]
     [6.9 3.1 5.1 2.3]
     [5.8 2.7 5.1 1.9]
     [6.8 3.2 5.9 2.3]
     [6.7 3.3 5.7 2.5]
     [6.7 3.  5.2 2.3]
     [6.3 2.5 5.  1.9]
     [6.5 3.  5.2 2. ]
     [6.2 3.4 5.4 2.3]
     [5.9 3.  5.1 1.8]]
    

**index numpy arrays**:  

**`np_var[list_index(row_in_2D)][element_index(column_in_2D]`**  
**OR**  
**`np_var[row, column]`**  
* As with indexing lists, **first element starts at "0"**  
* **Square brackets** to index  
* **Change** element with **"="**, this will make change to original array  
* When indexing multiple dimension arrays, start with highest level  
* Indexing 1D arrays will only require element index  
* Indexing a **3D** array would be **`np_var[slice, row, column]`**  


```python
# indexing a 1D nd array

A = np.array([1,3,5,6])

print(A)

A[2]
```

    [1 3 5 6]
    




    5




```python
# indexing a multidimensional array
# note how Python prints out for easier viewing of dimensions

array = np.array([[[3,4],[5,6]],[[7,8],[9,10]]])

print(array, "\n")

print(array[1][0][1])        # assessing element value "8" 
print(array[1,0,1])          # assessing same element
```

    [[[ 3  4]
      [ 5  6]]
    
     [[ 7  8]
      [ 9 10]]] 
    
    8
    8
    


```python
# changing 3rd element of nd array "a"
# note this will make change to the original array

print(A)

A[2] = 70
print(A)
```

    [1 3 5 6]
    [ 1  3 70  6]
    

**slice nd array**:  

**`np_var[index:index]`** 

**slice 2D array**:

**`np_var[row_indexFrom:row_indexTo,col_indexFrom:col_indexTo]`**  
* Same as slicing lists and tuples  
* **Square brackets**  
* Change selected elements with **"="**, this will make change to original array  
* When changing elements, cannot use this method to add extra elements, however can change more than one element to the same thing  
* **Note how Python prints arrays** for easier viewing of diemensions and more like tables, when slicing 2D arrays this can be helpful as first index refers to the row and second index refers to the column  


```python
# slicing and changing elements 

print("array before:", A)

A[1:3] = 5
print("array after:", A)
```

    array before: [ 1  3 70  6]
    array after: [1 5 5 6]
    


```python
A[1:3] = 7, 15
A
```




    array([ 1,  7, 15,  6])




```python
# slicing a multidimensional array

Arr = np.array([[1,2],[3,4],[5,6]])

print("array:\n\n", Arr, "\n")

print("slice [0:2,1]:\n\n", Arr[0:2,1])
```

    array:
    
     [[1 2]
     [3 4]
     [5 6]] 
    
    slice [0:2,1]:
    
     [2 4]
    

**obtain data type of nd array**:  

**`np_var.dtype`**  
* Will return datatype of "np_var"  


```python
# obtaining datatype for an nd array (here a 64 bit integer)

A.dtype
```




    dtype('int32')



**number of elements in nd array**:  

**`np_var.size`**  
* Will return number of elements in nd array


```python
# obtaining number of elements in nd array "a"

A.size
```




    4



**number of dimensions in nd array**:  

**`np_var.ndim`**  
* Will return number of dimensions in nd array  
* Think of this as how many nested lists there are i.e. **number of levels NOT number of lists at bottom level** as this would be the arrays shape,  
e.g. **`1D = array( [...] )` `2D = array( [[...],[...],[...]] )` `3D = array( [[[...],[...]]] )`**  


```python
# obtaining number of dimensions in nd array

A.ndim
```




    1



**shape: size of nd array in each dimension**:  

**`np_var.shape`**  
* Will return number of elements in each dimension (direction)  


```python
# obtaining shape of nd array

A.shape
```




    (4,)




```python
# example demonstraiting dimensions, shape & size
# note how Python prints out array for easier viewing of dimensions


a = [[[1],[2]],[[3],[4]],[[5],[6]],[[7],[8]]]



A = np.array(a)
print(A, "\n")
print("Dimensions:", A.ndim, ", count number of levels to first element")
print("Shape:", A.shape)
print("Size:", A.size, ", total number of elements")
```

    [[[1]
      [2]]
    
     [[3]
      [4]]
    
     [[5]
      [6]]
    
     [[7]
      [8]]] 
    
    Dimensions: 3 , count number of levels to first element
    Shape: (4, 2, 1)
    Size: 8 , total number of elements
    

**unique** function:  

**`np.unique(np_var, return_index=False, return_inverse=False, return_counts=False, axis=None)`**  
* Returns the sorted unique elements of an array  
* If **`return_index=True`** also return the indices of **`np_var`** that result in the unique array  
* If **`return_inverse=True`** also return the indices of the unique array that can be used to reconstruct **`np_var`**  
* If **`return_counts=True`** also return the number of times each unique item appears in **`np_var`**  


```python
# Using unique function

arr = np.array([5,2,6,2,7,5,6,8,2,9])

print("unique:", np.unique(arr))
print("return_index:", np.unique(arr, return_index=True))
print("return_inverse:", np.unique(arr, return_inverse=True))
print("return_counts:", np.unique(arr, return_counts=True))
```

    unique: [2 5 6 7 8 9]
    return_index: (array([2, 5, 6, 7, 8, 9]), array([1, 0, 2, 4, 7, 9], dtype=int64))
    return_inverse: (array([2, 5, 6, 7, 8, 9]), array([1, 0, 2, 0, 3, 1, 2, 4, 0, 5], dtype=int64))
    return_counts: (array([2, 5, 6, 7, 8, 9]), array([3, 2, 2, 1, 1, 1], dtype=int64))
    

**array addition / subtraction**:  

**`np_var3 = np_var +/- np_var2`**  
* Arrays can be added / subtracted  
* Arrays must be **SAME SHAPE** to be added or subtracted together  
* Will add or subtract elements of the same position  
* Can **add/subtract scalers** to a **single array** in a similar way  
* Can also **add/subtract vectors**, known as **broadcasting**  
(another array containing the same number of elements as the 1D part of the array) e.g.:  
$\;\;\;\;$**`matrix = np.array([[1,2,3],[4,5,6]])`**  
$\;\;\;\;$**`vector = np.array([0.5 ,0.25,0.8 ])`**  
$\;\;\;\;$**`matrix + vector = ([1.5 ,2.25,3.8 ],[4.5 ,5.25,6.8 ])`**  
    * **Above** example would **broadcast** across the **columns** (3 elements in the vector, and 3 columns in the matrix)  
    * To **broadcast** across the **rows**, vector must be in the **same shape** as the **matrix**, for the above, the vector would be:  
$\;\;\;\;$**`np.array([[0.25], [0.5]])`**  
* Results in another array of the same size as those added or subtracted together  

![](https://mathinsight.org/media/image/image/vector_2d_add.png "Vector addition")


```python
# example of array addition

a = np.array([[1,2,3],[4,5,6]])

print("original array:\n", a, "\n")
print("array + 2.5:\n", a+2.5)
```

    original array:
     [[1 2 3]
     [4 5 6]] 
    
    array + 2.5:
     [[3.5 4.5 5.5]
     [6.5 7.5 8.5]]
    


```python
# example of matrix addition

U = np.array([[2,4,5],[2,3,6]])
V = np.array([[3.2,5,1],[3,2,1]])

Z = U + V
print("Array U:\n", U, "\n")
print("Array V:\n", V, "\n")
print("Array U+V:\n", Z)
```

    Array U:
     [[2 4 5]
     [2 3 6]] 
    
    Array V:
     [[3.2 5.  1. ]
     [3.  2.  1. ]] 
    
    Array U+V:
     [[5.2 9.  6. ]
     [5.  5.  7. ]]
    


```python
# example of broadcasting a vector across columns

matrix = np.array([[1,2,3],[4,5,6]])
vector = np.array([0.25 ,0.5,0.75 ])
matrixAddVector = matrix + vector

matrixAddVector
```




    array([[1.25, 2.5 , 3.75],
           [4.25, 5.5 , 6.75]])




```python
# example of broadcasting a vector across rows

matrix = np.array([[1,2,3],[4,5,6]])
vector = np.array([[0.25], [0.5]])
matrixAddVector = matrix + vector

matrixAddVector
```




    array([[1.25, 2.25, 3.25],
           [4.5 , 5.5 , 6.5 ]])



**array multiplication**:  

**`np_var2 = #timesToMultiply * np_var`**  
* This will multiply the array by a scalar  
* A constant can also be added or subtracted to every element in a similar way (this is called **Broadcasting**)  


```python
# example of array multiplication

U = np.array([1,2,5])
X = 3 * U
X
```




    array([ 3,  6, 15])




```python
# example of Broadcasting, adding a constant

c = 3

Z = X + c
Z
```




    array([ 6,  9, 18])



**add axis to array**:  

**`newArrayVar = arrayVar[:,:,np.newaxis]`**  
* The number of passed dimensions ( **`:,`** ) should match the current arrays shape  


```python
# Adding an axis to an array

someArray = np.array([[1,2,3],[4,5,6]])

newArray = someArray[:,:,np.newaxis]

print("someArray:\n", someArray.shape, "\n")
print("newArray:\n", newArray.shape)
```

    someArray:
     (2, 3) 
    
    newArray:
     (2, 3, 1)
    

**hadamard product ( X ◦ Y )**:  

**`np_var3 = np_var * np_var2`**  
* Each element in corresponding positions will be multiplied together producing an array of equal shape  
* **Arrays must** be of **equal size** 
* See matrix multiplication for arrays of larger dimensions  


```python
# example of Hadamard product

U = np.array([1,2,5])
V = np.array([3,2,2])

Z = U * V
Z
```




    array([ 3,  4, 10])




```python
# another example of Hadamard product with 2D array

X = np.array([[1,2],[4,6]])
Y = np.array([[3,2],[2,3]])

Z = X * Y
Z
```




    array([[ 3,  4],
           [ 8, 18]])



**dot product / scalar product ( X · Y )**:  

**`np.dot(np_var1, np_var2)`**  
OR  
**`np_var1 @ np_var2`**  
* Among other things, the dot product can be used to test if two vectors are **perpendicular**, this will be shown if the dot product is **== 0**  
* Arrays **must be compatible size** (n x m, m x p) -> (n x p)  
* np.matrix can be used instead of arrays, when multiplying with np.matrix, dot product can be obtained with **\***, however be careful, as **\*** with arrays will try to broadcast rather than calculate the dot product  


```python
# example of scalar dot product

U = np.array([1,7])
V = np.array([21,1])

np.dot(U,V)
```




    28



**matrix multiplication**:  

**`np.dot(np_var1, np_var2)`**  
* **Matrix A's number of columns must be equal to Matrix B's number of rows** to be able to muliply matrices  
* **Different** process to that of 1D array dot product  
* Assisn to new array variable to save  
* NOTE - **`originalMatrix @ inverseOfMatrix = IdentityMatrix`** (Matrix multiplied by its inverse will give the matrix of 1's on the main diagonal and zeros everywhere else)  
* Creates a new array by obtaining the dot product of Matrix A's i'th row to Matrix B's j'th column:  

**1st row, 1st column:**  
1x7 + 2x9 + 3x11 = 58![](https://www.mathsisfun.com/algebra/images/matrix-multiply-a.svg "matrix mulitiplication")  

**1st row, 2nd column:**  
1x8 + 2x10 + 3x12 = 64![](https://www.mathsisfun.com/algebra/images/matrix-multiply-b.svg "matrix mulitiplication")  

**completed:**
![](https://www.mathsisfun.com/algebra/images/matrix-multiply-c.svg "matrix mulitiplication")


```python
# example of matrix multiplication

A = np.array([[0,1,1],[1,0,1]])
B = np.array([[1,1],[1,1],[-1,1]])

print("Matrix A:\n",A,"\n")
print("Matrix B:\n",B,"\n")

C = np.dot(A,B)
print("Matrix AB =\n",C)
```

    Matrix A:
     [[0 1 1]
     [1 0 1]] 
    
    Matrix B:
     [[ 1  1]
     [ 1  1]
     [-1  1]] 
    
    Matrix AB =
     [[0 2]
     [0 2]]
    

**Norm of a matrix or vector:**  

**`np.linalg.norm(np_var)`**  
* Returns the Frobenius norm by default (Squareroot of the sum of all squared elements)  


```python
# Return the frobenius norm of a matrix

A = np.array([[0,-4],
              [3,3],
              [-4,0]])
np.linalg.norm(A)
```




    7.0710678118654755



**transpose a matrix**:  

**`np_var.T`**  
* Keyword **T** will transpose an array or matrix (flips a matrix over its diagonal which switches the row and column indices to create a new matrix)  


```python
# example of transposing a matrix

# create an array
array = np.array([[1,1],[2,2],[3,3]])
print("Original array:\n",array,"\n")

# transpose array
transposed = array.T
print("Transposed array:\n",transposed)
```

    Original array:
     [[1 1]
     [2 2]
     [3 3]] 
    
    Transposed array:
     [[1 2 3]
     [1 2 3]]
    

**trace of a matrix:**  

**`np.trace(np_array_var)`**  
* Computes sum of elements[i, i+row index]  
* The trace of a matrix is the **sum of the main diagonal elements**  
* Note a trace of a matrix **ONLY exits** for a **square matrix**, however if array/matrix is not square in numpy, it still computes because **numpy trace does NOT include a check for square matrix**    


```python
# Trace of a matrix/array

A = np.matrix([[1,2,3],
              [3,4,5],
              [4,5,7]])

np.trace(A)
```




    12



**determinant of a matrix:**  

**`np.linalg.det(np_array_var)`**  
* Array/matrix **MUST** be **square**  
* Calculates the determinant of a matrix (sum of products of elements of any row or column and theri corresponding cofactors)  
* Note numpy uses approximations to calculate determinants and so **may not be accurate**  


```python
# Determinant of a matrix

A = np.matrix([[1,2,3],
              [3,4,5],
              [4,5,7]])

np.linalg.det(A)
```




    -1.9999999999999998



**inverse of a matrix:**  

**`np.linalg.inv(np_array_var)`**  
OR  
**`matrixVar.I`**  
* Returns the **inverse** of an array or matrix   
* Array/matrix **MUST** be **square**  
* **`.I`** method **ONLY** works on **numpy matrix** objects  
* NOTE - **`originalMatrix @ inverseOfMatrix = IdentityMatrix`** (Matrix multiplied by its inverse will give the matrix of 1's on the main diagonal and zeros everywhere else)  


```python
# Get inverse of an array

A = np.array([[6,2],
              [1,2]])

print(np.linalg.inv(A))
```

    [[ 0.2 -0.2]
     [-0.1  0.6]]
    


```python
# Get inverse of a numpy matrix

B = np.matrix([[6,2],
              [1,2]])

print(B.I)
```

    [[ 0.2 -0.2]
     [-0.1  0.6]]
    

**Moore-Penrose pseudoinverse of a matrix:**  

**`np.linalg.pinv(np_array_var)`**  
* **Non-square matrix** version of matrix **inverse**  
* **A<sup>+</sup>· A = I** &emsp; but &emsp; **A · A<sup>+</sup> ≠ I**  
* Note numpy approximates, and so sometimes this can be **inaccurate**  


```python
# Moore-Penrose pseudoinverse of a matrix

A = np.matrix([[7,2],
              [3,4],
              [5,3]])

np.linalg.pinv(A)
```




    matrix([[ 0.16666667, -0.10606061,  0.03030303],
            [-0.16666667,  0.28787879,  0.06060606]])




```python
# A+.A   -  Should equal identity matrix, but note this can sometimes not work correctly

np.linalg.pinv(A) @ A
```




    matrix([[1.00000000e+00, 2.70616862e-16],
            [2.63677968e-16, 1.00000000e+00]])



**eig function:**  

**`np.linalg.eig(np_var)`**  
* Returns the eigenvalues as an array (w) and corresponding eigenvectors as another array (v)  


```python
A = np.array([[1,0,-1],
              [1,0,0],
              [-2,2,1]])

np.linalg.eig(A)
```




    (array([ 2., -1.,  1.]),
     array([[ 6.66666667e-01,  4.08248290e-01,  7.07106781e-01],
            [ 3.33333333e-01, -4.08248290e-01,  7.07106781e-01],
            [-6.66666667e-01,  8.16496581e-01,  5.66950743e-17]]))



**min** method:  

**`np_var.min(axis=None)`**  
* Returns lowest value in array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  


```python
# Creating 2D array

array = np.array([[3,5,7],[1,2,3]])

array
```




    array([[3, 5, 7],
           [1, 2, 3]])




```python
# Get lowest value of all elements
array.min()
```




    1




```python
# Get lowest value of each column
array.min(axis=0)
```




    array([1, 2, 3])




```python
# Get lowest value of each row
array.min(axis=1)
```




    array([3, 1])



**max** method:  

**`np_var.max(axis=None)`**  
* Will return higest value element  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  


```python
# Get highest value of all elements
array.max()
```




    7




```python
# Get highest value of each column
array.max(axis=0)
```




    array([3, 5, 7])




```python
# Get highest value of each row
array.min(axis=1)
```




    array([3, 1])



**square root** method:  

**`np.sqrt(np_var)`**  
* Calculates square root of **each element** in an array  


```python
np.sqrt(array)
```




    array([[1.73205081, 2.23606798, 2.64575131],
           [1.        , 1.41421356, 1.73205081]])



**mean of array elements**:  

**`np_var.mean(axis=None)`**  
* Calculates mean (average) of all elements in an array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Mean** is denoted by the following symbols:  
    * **μ** - (mu) population parameter, i.e. the mean of the entire population  
    * **x̅** - (x-bar) is the mean of a sample  


```python
# Calculating mean of all elements

array.mean()
```




    3.5




```python
# Calculating mean across columns
array.mean(axis=0)
```




    array([2. , 3.5, 5. ])




```python
# Calculating mean across rows
array.mean(axis=1)
```




    array([5., 2.])



**variance of elements**:  

**`np_var.var(axis=None)`**  
**OR**  
**`((np_var.mean( ) - np_var)**2).sum( ) / np_var.size`**  
* * Returns variance of the elements in the array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Variance measures the average degree to which each point differs from the mean**  
* **Variance is the average of all data points within a group**  
* **Variance gives an actual value to how much the numbers in a data set vary from the mean**  
* **Variance** is denoted by **σ$^2$** (sigma squared)  

**Defined:**  

$\sigma^2(x) = \frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2$


```python
# Calculating the variance manually and with numpy method

var = ((array.mean() - array)**2).sum()/array.size
print(var)

print(array.var())
```

    3.9166666666666665
    3.9166666666666665
    

**standard deviation of elements**:  

**`np_var.std(axis=None)`**  
**OR**  
**`np.sqrt(((np_var.mean( ) - np_var)**2).sum( ) / np_var.size)`**  
* Returns standard deviation of the elements in the array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Standard deviation** is the **spread of a group of numbers from the mean**  
* **Standard deviation is the square root of the variance**  
* **Standard deviation** is a statistical measure that people can use **to determine how spread out numbers are in a data set** 
* **Standard deviation** is denoted by **σ** (sigma)  

**Defined:**  
$\sigma(x) = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2}$  

**Normal distribution:**  
![](https://i.insider.com/546e68776bb3f74f68b7d0ba?width=769&format=jpeg)


```python
# Calculating standard deviation of all elements in 3 different ways

std = np.sqrt(((array.mean() - array)**2).sum()/array.size)
print(std)

print(np.sqrt(var))

print(array.std())
```

    1.9790570145063195
    1.9790570145063195
    1.9790570145063195
    


```python
# standard deviation of columns
array.std(axis=0)
```




    array([1. , 1.5, 2. ])




```python
# standard deviation of rows
array.std(axis=1)
```




    array([1.63299316, 0.81649658])



**access value of pi π**:  

**`np.pi`**  
* Will return value of Pi


```python
# accessing value of Pi

np.pi
```




    3.141592653589793



**Random numbers with NumPy**:  

Part of NumPy library, option to import just package:  
**`from numpy import random`**  

**Random int**:  

**`np.random.randint(low, high=None, size=None)`**  
* Returns a random int  
* **`low`** = lowest integer to be drawn from distribution  
* **`high`** = if provided, this is one above the largest initeger to be drawn  
* **`size`** = output shape  
* If **only 1 parameter** provided, this is taken as the high value and low = 0   


```python
# Generates a 2D array with 2 rows and 6 columns containing random elements between 0 and 4

np.random.randint(5,size=(2,6))
```




    array([[2, 4, 0, 3, 1, 1],
           [4, 3, 2, 4, 4, 0]])



**Random float**:  

**`np.random.rand(d0,d1...dn)`**  
* Returns a random float between 0 and 1
* **`d0, d1...dn`** is optional and defines the return shape  


```python
# Generate a random float between 0 and 1

np.random.rand()
```




    0.17246702543612125




```python
# Generate a 2D array with 3 rows and 2 columns populated with random floats between 0 and 1

np.random.rand(3,2)
```




    array([[0.09840245, 0.26421107],
           [0.05817485, 0.54406616],
           [0.72444541, 0.96487634]])



**Random Seed**:  

**`np.random.seed(self, seed=None)`**  
* The random number generator needs a number to start with (a seed value), to be able to generate a random number  
* By default the random number generator uses the current system time  
* Use the seed() method to customize the start number of the random number generator  
* Note: If you use the same seed value twice you will get the same random number twice  


```python
# Random float using system time (run cell multiple times)

np.random.rand()
```




    0.678933210162206




```python
# Sets seed to 10, will return the same random number each time its run

np.random.seed(10)
np.random.rand()
```




    0.771320643266746



**Random Binomial**:  

Binomials have:  
* A fixed number of trials  
* Only have 2 possible outcomes  
* the outcomes are independent of each other  
* the probability of success remains the same for each trial  

**`np.random.binomial(n, p, size=None)`**  
* **`n`** is number or trials per experiment  
* **`p`** is probability of sucess. In the interval [0,1]  
* **`size`** Number of times to run the experiment, default None = 1
* **Returns number of successes for each experiment**  


```python
# Example, we roll 2 dice 5 times in each experiment
# The probability of a double is 1/36
# We run the experiment 10 times
# Output will be how may successes in each experiment

np.random.binomial(5, (1/36), size=10)
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])




```python
# importing pyplot for examples below

from matplotlib import pyplot as plt
```

**Random Uniform**:  

**`np.random.uniform(low=0.0, high=1.0, size=None)`**  
* Generates random numbers between low and high (inclusive) with equal probability  
* **`size`** is samples drawn  


```python
# 1000 random samples between 0 and 1 (inclusive)

samples = np.random.uniform(0, 1, size=1000)
plt.hist(samples)
plt.show()
```


    
![png](%23%20NumPy_files/%23%20NumPy_123_0.png)
    


**Random Poisson**:  

**`np.random.poisson(lam=1.0, size=None)`**  
* **`lam`** is expectation of interval, must be >= 0  
* **`size`** is samples drawn  


```python
samples = np.random.poisson(lam=3, size=1000)
plt.hist(samples)
plt.show()
```


    
![png](%23%20NumPy_files/%23%20NumPy_125_0.png)
    


**Random Normal Distribution**:  

**`np.random.randn(d0,d1,...dn)`**  
* **`d0,d1,...dn`** is the dimentions of the returned array, **must be non-negative**  


```python
# 1000 samples from normal distribution

samples = np.random.randn(1000)
plt.hist(samples)
plt.show()
```


    
![png](%23%20NumPy_files/%23%20NumPy_127_0.png)
    


**Random Gassian distribution**:  

**`Normal distribution * σ + μ`**  
* See above for normal distribution  
* **`σ`** is **standard deviation**  
* **`μ`** is **mean**  


```python
# Gassian distribution

mu=5
sigma=2

# 1000 samples
for n in range(100,1001,100):
    samples = np.random.randn(n) * sigma + mu 
    
plt.hist(samples)
plt.show()
```


    
![png](%23%20NumPy_files/%23%20NumPy_129_0.png)
    


**linspace**:

**`np.linspace(start, stop, num= #samples_to_generate)`**  
* Returns evenly spaced numbers from **"start" to "stop"**  
* **"num="** is parameter which defines how many samples to produce, defaults to 50  
* Prounounced "line space"  


```python
# example of linspace (line space)  

np.linspace(-5,10,num=31)
```




    array([-5. , -4.5, -4. , -3.5, -3. , -2.5, -2. , -1.5, -1. , -0.5,  0. ,
            0.5,  1. ,  1.5,  2. ,  2.5,  3. ,  3.5,  4. ,  4.5,  5. ,  5.5,
            6. ,  6.5,  7. ,  7.5,  8. ,  8.5,  9. ,  9.5, 10. ])



**matplotlib**:  

[Link to info on matplotlibs colourmap](https://matplotlib.org/stable/tutorials/colors/colormaps.html)

* MatPlotLib is a library used to creat static, animated, and interactive visualizations in Python  
* Below is an example using MatPlotLib to plot a graph using some methods talked about above  


```python
# import library to help plot diagram

import matplotlib.pyplot as plt
```


```python
# displays plot in jupyter notebook

%matplotlib inline
```


```python
# generate 100 samples from 0 to 2π
X = np.linspace(0,2*np.pi,num=100)

# map array "x" to new array "y" applying sin to each element in the array
Y = np.sin(X)
```


```python
# draw diagram with array "x" on x-axis and array "y" on y-axis

plt.plot(X,Y)
```




    [<matplotlib.lines.Line2D at 0x15f8e5264c0>]




    
![png](%23%20NumPy_files/%23%20NumPy_136_1.png)
    


**subplots**:  

**`plt.subplot(numberRows=1, numberCols=1, index=1)`**  
* Plots several images in the same cell  


```python
# subplots

for i in range(1, 7):
    plt.subplot(2, 3, i)
    plt.text(0.5, 0.5, str((2, 3, i)),
             fontsize=18, ha='center')
```


    
![png](%23%20NumPy_files/%23%20NumPy_138_0.png)
    


[<p style="text-align: right;">**⬆ Top of Page ⬆**</p>](#NumPy)

---
