
##   مدلسازی خطی با استفاده از NumPy و scikit-learn

### مقدمه
در این پروژه، ما تلاش کردیم تا یک مدل خطی را برای داده‌هایی که در فایل `dataset.csv` آمده است، با استفاده از دو روش مختلف، یعنی NumPy و scikit-learn ایجاد کنیم. همچنین، خطاها و نتایج به دست آمده را تجسم کرده و در یک گزارش نوشته‌ایم.

### کدهای استفاده شده

#### 1. خواندن داده‌ها
```python
import pandas as pd

# خواندن داده‌ها از فایل CSV با جداکننده کاما
data = pd.read_csv('dataset.csv')
```

#### 2. تعیین متغیرهای ورودی و خروجی
```python
# تعیین متغیرهای ورودی (X) و خروجی (y)
X = data[['x1', 'x2']]
y = data['y']
```

#### 3. مدلسازی با استفاده از NumPy
```python
import numpy as np

# روش مدلسازی ماتریسی با استفاده از NumPy
X_transpose = np.transpose(X)
XtX_inverse = np.linalg.inv(np.dot(X_transpose, X))
Xty = np.dot(X_transpose, y)
weights_numpy = np.dot(XtX_inverse, Xty)
```

#### 4. مدلسازی با استفاده از scikit-learn
```python
from sklearn.linear_model import LinearRegression

# روش مدلسازی با استفاده از scikit-learn
model_sklearn = LinearRegression()
model_sklearn.fit(X, y)
weights_sklearn = [model_sklearn.intercept_] + list(model_sklearn.coef_)
```

#### 5. نمایش وزن‌ها و تجسم داده‌ها
```python
import matplotlib.pyplot as plt

# چاپ وزن‌ها
print("Weights (NumPy):", weights_numpy)
print("Weights (scikit-learn):", weights_sklearn)

# تجسم داده‌ها و خط مدل
plt.scatter(data['x1'], data['y'], label='Data Points')
plt.plot(data['x1'], weights_sklearn[0] + weights_sklearn[1]*data['x1'] + weights_sklearn[2]*data['x2'], color='red', label='Regression Line')
plt.xlabel('x1')
plt.ylabel('y')
plt.legend()
plt.show()
```

با انجام این پروژه، مدل‌های خطی با استفاده از NumPy و scikit-learn برای داده‌های ورودی مشخص ساخته شدند. همچنین نتایج و خطاها به صورت گرافیکی نمایش داده شده‌اند.

Last updated on: 2024-02-12

Last updated on: 2024-02-14

Last updated on: 2024-02-25

Last updated on: 2024-02-25

Last updated on: 2024-02-28

Last updated on: 2024-02-28

Last updated on: 2024-03-02

Last updated on: 2024-03-04

Last updated on: 2024-03-08

Last updated on: 2024-03-08

Last updated on: 2024-03-11

Last updated on: 2024-03-19

Last updated on: 2024-03-22

Last updated on: 2024-03-25

Last updated on: 2024-03-26

Last updated on: 2024-03-28

Last updated on: 2024-03-29

Last updated on: 2024-04-04

Last updated on: 2024-04-05

Last updated on: 2024-04-07

Last updated on: 2024-04-11

Last updated on: 2024-04-16

Last updated on: 2024-04-17

Last updated on: 2024-04-17

Last updated on: 2024-04-18

Last updated on: 2024-04-19

Last updated on: 2024-04-23

Last updated on: 2024-04-24

Last updated on: 2024-04-27

Last updated on: 2024-04-28

Last updated on: 2024-05-02

Last updated on: 2024-05-03