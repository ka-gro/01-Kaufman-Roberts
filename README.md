# 01-Kaufman-Roberts
```
M = 2
V = 3
t = [1, 2]
a = [[4/10, 1]]

def calc_x(V, M, a, t):
    x = [1] * (V + 1)
    for n in range(1, V + 1):
    	sum = 0
    	for i in range(0, M):
    	    if n>=t[i]: 
    	        sum += a[i] * t[i] * x[n - t[i]]
    	x[n] = sum / n
    return x
        
def calc_po(x):
	sum = 0
	for item in x:
	    sum += item
	return 1 / sum

def calc_pn(x, V, M, a, t):
    P = [1] * (V + 1)
    P[0] = calc_po(x)
    for n in range(1, V + 1):
    	sum = 0
    	for i in range (0, M):
    	    if n>=t[i]: 
    	        sum += a[i] * t[i] * P[n - t[i]]
    	P[n] = sum/n
    return P

def calc_bn(P, V, t, i = 1):
    sum = 0
    for n in range (V-t[i-1] + 1, V + 1): 
        sum += P[n]
    return sum

def calc_all(M, V, a, t):
    x = calc_x(V, M, a, t)
    P = calc_pn(x, V, M, a, t)
    b1 = calc_bn(P, V, t, 1)
    b2 = calc_bn(P, V, t, 2)
    print(x, "\n", P, "\n", b1, "\n", b2)

for item in a:
    calc_all(M, V, item, t)
    print("\n")
```
