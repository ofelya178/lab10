import math

def f(x):
    return x - math.atan(x ** (1/3))

def df(x):
    if x == 0:
        return float('inf')  # 0-da törəmə sonsuz olur, bölməyə səbəb ola bilər
    return 1 - (1 / (3 * (1 + x ** (2/3)) * x ** (2/3)))

def newton_method(f, df, x0, tol=1e-6, max_iter=100):
    x = x0
    for i in range(max_iter):
        fx = f(x)
        dfx = df(x)
        if dfx == 0:
            raise ValueError("Törəmə sıfıra bərabər oldu")
        x_new = x - fx / dfx
        if abs(x_new - x) < tol:
            return x_new
        x = x_new
    raise Exception("Maksimum iterasiya sayına çatıldı")

root = newton_method(f, df, x0=0.5)
print("Təqribi kök:", root)
