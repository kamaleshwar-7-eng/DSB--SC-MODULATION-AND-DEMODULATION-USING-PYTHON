# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

 __Program__:
 ```python
import numpy as np
import matplotlib.pyplot as plt

Am = 9.7
Ac = 19.4

fm = 366
fc = 3660

fs = 36600

t = np.arange(0, 1/fm, 1/fs)

m = Am * np.cos(2 * np.pi * fm * t)

c = Ac * np.cos(2 * np.pi * fc * t)

dsb_sc = m * c

plt.subplot(3,1,1)
plt.plot(t, m)
plt.title("Message Signal m(t)")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")

plt.subplot(3,1,2)
plt.plot(t, c)
plt.title("Carrier Signal c(t)")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")

plt.subplot(3,1,3)
plt.plot(t, dsb_sc)
plt.title("DSB-SC Modulated Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")

plt.tight_layout()
plt.show()
```
   __Output__:
   
<img width="801" height="602" alt="DSBSC Modulation using python" src="https://github.com/user-attachments/assets/5e031dc9-1f4b-4cfc-af55-3543587f4c99" />

   __Result__:

   Thus DSB--SC-Modulation-and-Demodulation-using-NumPy-and-Matplotlib is experimentally done and the output is verified
