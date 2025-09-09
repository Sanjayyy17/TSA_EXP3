# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np

# Given data
data = [3, 16, 156, 47, 246, 176, 233, 140, 130, 101, 166, 201, 200, 116, 118, 
        247, 209, 52, 153, 232, 128, 27, 192, 168, 208, 187, 228, 86, 30, 151, 
        18, 254, 76, 112, 67, 244, 179, 150, 89, 49, 83, 147, 90, 33, 6, 158, 
        80, 35, 186, 127]

lags = range(35)

# Convert to numpy array
data = np.array(data)
N = len(data)

# Mean and variance
mean = np.mean(data)
var = np.var(data)

# Normalize data
normalized = data - mean

# Pre-allocate autocorrelation values
acf_values = []

# Compute autocorrelation for each lag
for lag in lags:
    num = np.sum(normalized[:N-lag] * normalized[lag:])
    den = (N - lag) * var
    acf = num / den
    acf_values.append(acf)

# Display the ACF graph
plt.figure(figsize=(10,5))
plt.stem(lags, acf_values, basefmt=" ")
plt.xlabel("Lags")
plt.ylabel("ACF")
plt.title("AutoCorrelation Function (First 35 Lags)")
plt.grid(True)
plt.show()

print("ACF values for first 35 lags:")
print(acf_values)

```
### OUTPUT:
<img width="1070" height="592" alt="image" src="https://github.com/user-attachments/assets/45cd02b1-686e-4d34-a066-c085adba4190" />
```
ACF values for first 35 lags:
[np.float64(1.0), np.float64(0.07476082838034886), np.float64(0.013973266220089913), np.float64(-0.04112859350635042), np.float64(0.14200940383221208), np.float64(-0.06563648175886712), np.float64(-0.0051045165268204925), np.float64(0.10266303374328971), np.float64(-0.06774179649581681), np.float64(0.03869031999271554), np.float64(0.08941293653388485), np.float64(0.06494547633850699), np.float64(0.01882097483613537), np.float64(0.10051019244367734), np.float64(-0.01689257403450788), np.float64(-0.19771396419637355), np.float64(0.005678222292194008), np.float64(0.038667532079130394), np.float64(-0.18262380340483123), np.float64(-0.002825790656029354), np.float64(0.10936822816475186), np.float64(-0.04416668786023051), np.float64(-0.1590231938242492), np.float64(-0.20157543776944775), np.float64(-0.3780723112834823), np.float64(-0.03200298055794217), np.float64(-0.05055796754334612), np.float64(0.12132384905867458), np.float64(-0.5184411654313342), np.float64(0.16366601385495996), np.float64(0.12394787064986804), np.float64(-0.11709494845851771), np.float64(-0.2559233097710428), np.float64(-0.010967773388143892), np.float64(-0.25304851390293415)]
```

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
