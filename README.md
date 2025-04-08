# IDEAL SAMPLING 
# Aim:
To study the concept of ideal sampling in signal processing and its effect on a continuous-time signal. The goal is to understand how sampling works under ideal conditions, such as perfect reconstruction and no aliasing.

# Tools Required:
MATLAB / Python (with libraries such as NumPy, SciPy, and Matplotlib)

To simulate the sampling process and visualize the waveforms.

Oscilloscope (optional) – If working with real hardware, for measuring continuous signals and sampling.

Signal Generator (optional) – To generate a continuous-time signal.
# program
#Impulse Sampling
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample
fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
# Output Waveform:

![B](https://github.com/user-attachments/assets/c86b1d87-ed0f-4d21-81f1-ea615f7554a5)
![2](https://github.com/user-attachments/assets/5ed720ef-7dd9-4e12-bcfd-a5190f32f1fc)
![3](https://github.com/user-attachments/assets/142a12ec-064e-4d29-860e-0a0d99a4dd78)


Continuous Signal: A smooth sine wave at the given frequency (10 Hz).

Ideal Samples: Red dots or stems placed at the discrete sample points with the given sampling frequency (50 Hz).

Reconstructed Signal: A green curve showing the signal reconstructed from the ideal samples using sinc interpolation, ideally matching the original continuous signal.

# Results:
Continuous Signal: The original signal, a smooth sine wave, is plotted as a continuous curve.

Ideal Sampling: The discrete points (samples) are perfectly spaced based on the sampling rate. In the ideal case, these samples contain all necessary information to reconstruct the signal without any loss.

Reconstruction: The reconstructed signal closely matches the continuous one, showing that the ideal sampling process and sinc interpolation allow for perfect signal reconstruction when sampling and reconstruction are done correctly.
