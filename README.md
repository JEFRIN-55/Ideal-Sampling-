# Ideal Sampling

## Aim
To perform ideal sampling on a continuous signal and analyze its reconstruction.

## Tools Required
- Python  
- NumPy  
- Matplotlib  
- SciPy  

## Program

### Impulse Sampling
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample

# Define parameters
fs = 100  # Sampling frequency
t = np.arange(0, 1, 1/fs)  # Time vector
f = 5  # Signal frequency
signal = np.sin(2 * np.pi * f * t)  # Continuous signal

# Plot continuous signal
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()

# Perform sampling
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)

# Plot sampled signal
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()

# Reconstruction using resampling
reconstructed_signal = resample(signal_sampled, len(t))

# Plot reconstructed signal
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
```
## Output Waveforms
- **Continuous Signal:** The original sinusoidal waveform.
  ![image](https://github.com/user-attachments/assets/12469376-fce2-41a4-93cc-5b4741b8405c)

- **Sampled Signal:** The signal obtained after impulse sampling.  
  ![image](https://github.com/user-attachments/assets/5f7ca442-870e-4726-8e46-f04efb1eb947)
  
- **Reconstructed Signal:** The resampled signal closely following the original.
  ![image](https://github.com/user-attachments/assets/36748c71-3b41-490a-97b7-562e1bd7ea5b)



## Results
- The continuous signal was successfully sampled using impulse sampling.  
- The reconstruction process demonstrates that an ideal sampled signal retains its original characteristics when resampled correctly.  
