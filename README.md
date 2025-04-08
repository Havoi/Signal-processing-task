So I have Used python to try solving this question . You will find all the plots and code in "q2.ipynb" . I will tell whatever I understood while solving this problem . So first I loaded the given audio to code with scipy wavefile.read functon . This function gives us the sampling frequency and the modulated wave array . So the sampling frequecy is 44.1k and audio file was about 2 seconds long so naturally the length of modulated array was around ~87 k . Then I made the times array which is a list containg all the times at which a sample was taken . Then plotted the modulated signal for the first 1000 samples (t[:1000] , modulated[:1000]) . Then I plotted fft of the modulated signal which scipy.fft function which made it really easy . I got to know online that in case of Amplitude Modulation , carrier frequency is usually the one with the highest magnitude. Now carrier frequency was calculated mathematically which I got around ~10.5 kHz . So to reverse modulate this carrier frequency I multiplied the modulated wave with cos(2pi * fc * t) which now leaves the high frequency jump . So then I designed a pretty standard band-pass filter (actually copied from internet) & gave the pass frequency as (300 ,4000) as nothing was mentioned about this band in the question . Then Plotted a pretty comparative graph Before and After Demodulation for the first 1000 samples. Working on this question really sparked my curiosity and made me learn new crazy things .

# 🎧 Modulated Audio Signal Processing

This repository contains my solution to the **Modulated Audio Signal Processing** task using Python. The goal was to demodulate a given AM (Amplitude Modulated) audio signal, clean it using a bandpass filter, and recover the original audio.

---

## 📁 Files Included

- `q2.ipynb` – Jupyter Notebook with full code and step-by-step explanation
- `modulated_noisy_audio.wav` – The original modulated input audio
- `filtered_output.wav` – The demodulated and cleaned audio output (if applicable)

---

## 🧠 My Approach & Learnings

### 1. **Loading the Audio**
- Used `scipy.io.wavfile.read()` to read the `.wav` file.
- Got a sampling frequency of **44.1 kHz**.
- Since the audio was ~2 seconds, it had around **87,000 samples**.

### 2. **Time Array Generation**
- Created a time array using:
  ```python
  t = np.arange(len(modulated)) / sampling_rate

