# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

## AIM:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

## APPARATUS REQUIRED:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

## Theory:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

## Procedure:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message
   
## Program:
```
import numpy as np
import matplotlib.pyplot as plt

Am=9.5
fm=520
Ac=19
fc=5200
fs=52000

t=np.arange(0, 3/fm, 1/fs)

m = Am*np.cos(2*3.14*fm*t)
plt.subplot(3,1,1)
plt.plot(t,m)

c = Ac*np.cos(2*3.14*fc*t)
plt.subplot(3,1,2)
plt.plot(t,c)

s1=(Ac+m)*np.cos(2*3.14*fc*t)
s2=(Ac-m)*np.cos(2*3.14*fc*t)

s=s1-s2
plt.subplot(3,1,3)
plt.plot(t,s)
```
## Output:
<img width="571" height="416" alt="image" src="https://github.com/user-attachments/assets/9d12f4e2-6639-453b-b0de-b7e9b43c3b89" />

## Tabulation:
![WhatsApp Image 2025-11-23 at 15 32 37_f0b0224d](https://github.com/user-attachments/assets/b4472083-cae1-4ac2-ac5c-b4683e324915)

## Result:
The DSB-SC experiment shows that the message signal is transmitted through only the sidebands while the carrier is suppressed. This makes the modulation more power-efficient. The output waveform and spectrum confirm the absence of the carrier. The original message is recovered using coherent detection.

