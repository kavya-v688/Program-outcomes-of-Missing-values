# Program-outcomes-of-Missing-values
  Python 3.9.7 (tags/v3.9.7:1016ef3, Aug 30 2021, 20:19:38) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license()" for more information.
>>> import numpy as np
>>> import pandas as pd
vals1
>>>  = np.array([1,None,3,4])
 
SyntaxError: unexpected indent
>>> vals1=np.array([1,None,3,4])
>>> vals1
array([1, None, 3, 4], dtype=object)
>>> for dtype in['object','int']:
	print("dtype=",dtype)
	%timeit np.arange(1E6,dtype=dtype
			  
SyntaxError: invalid syntax
>>> for dtype in ['object','int']:
	print("dtype =",dtype)
	%timeit np.arange(1E6,dtype=dtype).sum()
	
SyntaxError: invalid syntax
>>> for dtype in['object','int']:
	print("dtype =",dtype)
	timeit np.arange(1E6,dtype=dtype).sum()
	
SyntaxError: invalid syntax
>>> print()

>>> vals1.sum()
Traceback (most recent call last):
  File "<pyshell#15>", line 1, in <module>
    vals1.sum()
  File "C:\Users\Hp\AppData\Local\Programs\Python\Python39\lib\site-packages\numpy\core\_methods.py", line 48, in _sum
    return umr_sum(a, axis, dtype, out, keepdims, initial, where)
TypeError: unsupported operand type(s) for +: 'int' and 'NoneType'
>>> vals2 =np.array([1,np.nan,3,4])
>>> vals2.dtype
dtype('float64')
>>> 1 + np.nan
nan
>>> 0 * np.nan
nan
>>> vals2.sum(), vals2.min(), vals2.max()
(nan, nan, nan)
>>> np.nansum(vals2), np.nanmin(vals2), np.nanmax(vals2)
(8.0, 1.0, 4.0)
>>> pd.Series([1,np.nan,2,None])
0    1.0
1    NaN
2    2.0
3    NaN
dtype: float64
>>> x = pd.Series(range(2), dtype=int)
>>> x
0    0
1    1
dtype: int32
>>> x[0] = None
>>> x
0    NaN
1    1.0
dtype: float64
>>> data = pd.Series([1, np.nan, 'hello', None])
>>> data.isnull()
0    False
1     True
2    False
3     True
dtype: bool
>>> data[data.notnull()]
0        1
2    hello
dtype: object
>>> data.dropna()
0        1
2    hello
dtype: object
>>> df = pd.DataFrame([[1, np.nan, 2],[2, 3, 5],[np.nan, 4, 6]])
>>> df
     0    1  2
0  1.0  NaN  2
1  2.0  3.0  5
2  NaN  4.0  6
>>> df.dropna()
     0    1  2
1  2.0  3.0  5
>>> df.dropna(axis='columns')
   2
0  2
1  5
2  6
>>> df[3] = np.nan
>>> df
     0    1  2   3
0  1.0  NaN  2 NaN
1  2.0  3.0  5 NaN
2  NaN  4.0  6 NaN
>>> df.dropna(axis='columns', how='all')
     0    1  2
0  1.0  NaN  2
1  2.0  3.0  5
2  NaN  4.0  6
>>> df.dropna(axis='rows', thresh=3)
     0    1  2   3
1  2.0  3.0  5 NaN
>>> data = pd.Series([1, np.nan, 2, None, 3], index=list('abcde'))
>>> data
a    1.0
b    NaN
c    2.0
d    NaN
e    3.0
dtype: float64
>>> data.fillna(0)
a    1.0
b    0.0
c    2.0
d    0.0
e    3.0
dtype: float64
>>> data.fillna(method='ffill')
a    1.0
b    1.0
c    2.0
d    2.0
e    3.0
dtype: float64
>>> data.fillna(method='bfill')
a    1.0
b    2.0
c    2.0
d    3.0
e    3.0
dtype: float64
>>> df
     0    1  2   3
0  1.0  NaN  2 NaN
1  2.0  3.0  5 NaN
2  NaN  4.0  6 NaN
>>> df.fillna(method='ffill', axis=1)
     0    1    2    3
0  1.0  1.0  2.0  2.0
1  2.0  3.0  5.0  5.0
2  NaN  4.0  6.0  6.0
>>>
