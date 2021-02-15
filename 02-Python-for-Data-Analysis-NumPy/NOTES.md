# numpy notes
Linear algebra library
vectors (1d arrays) and matricies (2d arrays)
cast list to array with array function (list of list for matrix)

## Generation & Modification Methods
- arange method (similar to range function)
- zeros or ones - array of all 0's or 1's, single digit for vector or tuple for matrix
- linspace - even distribution of array values over a range 
- eye - identity matrix, single parameter, 2D square matrix w/ diagonal of 1's, all other values are 0
- random generation of arrays - many different methods
	- rand - populate w/ random samples with uniform distribution between 0 and 1 - vector or matrix
	- randn - from a standard uniform (Gausian) distribution centered around 0
	- randint - random integers between low & high range
- reshape - return same array reshaped with new dimensions - cannot resize - convert vector to matrix & visa versa
- max, min, argmax or argmin for index location
- shape - returns shape as tuple 
- dtype - data type in array

## Indexing & Selection
- brackets & slices
- broadcast - set with slices arr[0:5] = 100, create slice var, will change original array too - not actual copy but reference
	- use copy method to create actual copy
- indexing matrix
	- double bracket format arr[0][0] or arr[0] for entire row
	- single bracket format with comma (recommended) arr[0,0]
	- slices [:2,1:]
- conditional selection
	- use logical operator (e.g. arr > 5) to get array of True/False
	- arr[bool_arr] to get only elements where bool_arr is True e.g. arr[arr>5]

## Operations
- array w/ array simple mathematical operators - add, subtract, multiply, division with 2 arrays
- array w/ scaler simple mathematical operators - add, subract, multiply, division, with normal number
- numply will ignore (only give warnings) for some errors, e.g. divide by 0, resulting value will be nan or inf
- universal functions
	- sqrt, exp, max/min, trig functions (sin, cos, tan), log