# algoritmic_complexcity

Poniżej przedstawienie sposobu działania dwóch funkcji fibo1() i fibo2(), które po otrzymaniu argumentu
obliczają i zwracają wyrazy ciągu Fibonacciego w ilosci równej wartości przekazanego argumentu. 
Funkcja fibo1() realizuje obliczenia za pomocą rekurencji, natomiast fibo2() w sposób iterracyjny.

Poniżej została przeprowadzona analiza wydajności czasowej obydwu funkcji w zależności od ilości wyrazów ciągu.
Wyniki zobrazowane zostały na wykresie.

### Realizacja obliczeń przez rekurencję 
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
```


### Realizacja obliczeń przez iterację 

```py
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
       
    return fib_list
```


### Funkcje do pomiaru czasu obliczeń. 
```py
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
```

### Przedstawienie wyników badań wydajności na wykresie dla 30 wyrazów ciągu (points=30).
```py
points = 30
tim_fibo_bad = [calculate_tim_fibo1(x) for x in range(1,points)]
tim_fibo_good = [calculate_tim_fibo2(x) for x in range(1,points)]
xpoints = [x for x in range(1,points)]

import matplotlib.pyplot as plt
import numpy as np

plt.plot(xpoints, tim_fibo_bad)
plt.plot(xpoints, tim_fibo_good)

plt.ylabel("Execution time")
plt.xlabel("Number of items")
plt.show()
```
![image](https://user-images.githubusercontent.com/111123372/200170133-47831ce0-2666-493c-9226-8b722186b607.png)

Z przeprowadzonych pomiarów, można wywnioskować,że lepszym sposobem do obliczenia n-tego wyrazu ciągu,
jest rozwiązanie z zastosowaniem iterracji. Na wykresie można zaobserwować, że dla funkcji fibo1() 
wraz ze wzrostem ilości wyrazów ciągu czas trwania obliczeń wzrasta wykładniczo i przy 30 wyrazie wynosi juz blisko pół sekundy, 
z przeprowadzonych wcześniej doświadczeń przy n=40, obliczenia w przypadku rekurencji trwały bardzo długo i prowadziły do zawieszenia komputera,
natomiast przy rozwioązaniu iterracyjnym fibo2() czas realizacji jest wciąż bliski zeru, nawet przy znacznej liczbie wyrazów.




