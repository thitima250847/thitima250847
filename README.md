def f(x):
    return x**3 + 3*x**2 - 1

def bisection_method(a, b, tol):
    if f(a) * f(b) >= 0:
        print("f(a) และ f(b) ต้องมีค่าต่างเครื่องหมาย")
        return None

    iteration = 0
    while (b - a) / 2 > tol:
        iteration += 1
        c = (a + b) / 2  # จุดกึ่งกลาง
        if f(c) == 0:
            # เจอรากที่แน่นอน
            break
        elif f(a) * f(c) < 0:
            b = c  # รากอยู่ในช่วง [a, c]
        else:
            a = c  # รากอยู่ในช่วง [c, b]

        print(f"Iteration {iteration}: a = {a}, b = {b}, c = {c}, f(c) = {f(c)}")

    return (a + b) / 2

# กำหนดค่าเริ่มต้น
a = 0
b = 1
tolerance = 1e-6

# เรียกใช้ฟังก์ชัน
root = bisection_method(a, b, tolerance)
if root is not None:
    print(f"รากของสมการคือ: {root}")

