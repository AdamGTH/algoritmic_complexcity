# algoritmic_complexcity
Przedstawienie złożoności obliczeniowej
```py
def fibo1(n):
    if n < 0:
        return False
    elif n == 0:
        return 1
    elif n > 0:
        return fibo1(n-1) + fibo1(n-2)
    else:
        return False

def fibo2(n):
    a = 1
    b = 1
    i = 0
    fib_list = []
    while(i < (n//2)):
        i = i + 1
        fib_list.append(a)
        fib_list.append(b)
        a = a+b
        b = a+b
    #print(fib_list)    
    return fib_list


from timeit import default_timer as timer

def calculate_tim_fibo1(n):
    start = timer()
    fibo1(n)
    end = timer()
    return end-start
    
def calculate_tim_fibo2(n):
    start = timer()
    fibo2(n)
    end = timer()
    return end-start

item = 30
tim_fibo_bad = [calculate_tim_fibo1(x) for x in range(1,item)]
tim_fibo_good = [calculate_tim_fibo2(x) for x in range(1,item)]
xpoints = [x for x in range(1,item)]

import matplotlib.pyplot as plt
import numpy as np

plt.plot(xpoints, tim_fibo_bad)
plt.plot(xpoints, tim_fibo_good)
plt.show()
```
![image](https://user-images.githubusercontent.com/111123372/200168196-8516426e-70da-4a5d-b18a-019211df167f.png)

