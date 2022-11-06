# algoritmic_complexcity
przedstawienie złożoności obliczeniowej
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

tim_fibo1 = [calculate_tim_fibo1(x) for x in range(1,30)]
tim_fibo2 = [calculate_tim_fibo2(x) for x in range(1,30)]

import matplotlib.pyplot as plt
import numpy as np

xpoints = [x for x in range(1,30)]

plt.plot(xpoints, tim_fibo1)
plt.plot(xpoints, tim_fibo2)
plt.show()
```
![pobrane (1)](https://user-images.githubusercontent.com/111123372/200167197-881f5674-c8cb-44f9-b6a5-02289f8ab7a4.png)

