AIM:
To write a program to perform DSBSC modulation and demodulation using SCI LAB and study its spectral characteristics.

EQUIPMENTS REQUIRED
• Computer with i3 Processor
• SCI LAB

Note: Keep all the switch faults in off position

ALGORITHM:
Define Parameters:
• Fs: Sampling frequency.
• T: Duration of the signal.
• Fc: Carrier frequency.
• Fm: Frequency of the message signal.
• Amplitude: Maximum amplitude of the message signal.
Generate Signals:
• Message Signal: A sinusoidal signal that will be modulated.
• Carrier Signal: A high-frequency sinusoidal signal used for modulation.
DSBSC Modulation:
• Modulated Signal: Multiply the message signal by the carrier signal to produce the DSBSC signal
DSBSC Demodulation:
• Multiplication: Multiply the modulated signal by the carrier signal to get the product of the message signal with itself (i.e., the original message signal plus high-frequency components).
• Low-pass Filtering: Apply a Butterworth low-pass filter to remove the high- frequency components and recover the original message signal.
Visualization:
Plot the message signal, carrier signal, DSBSC modulated signal, and the recovered signal after demodulation.
PROCEDURE
• Refer Algorithms and write code for the experiment.
• Open SCILAB in System
• Type your code in New Editor
• Save the file
• Execute the code
• If any Error, correct it in code and execute again
• Verify the generated waveform using Tabulation and Model Waveform

MODEL GRAPH:
image
PROGRAM:
  clc;  
  clear;  
  close;  
  
  Am = 8.8;   
  fm = 863;   
  fs = 863000;   
  fc = 8630;   
  Ac = 17.6;   
  t = 0:1/fs:2/fm;  
  
  m = Am * cos(2 * %pi * fm * t);  
  subplot(4,1,1);  
  plot(t, m);  
  title('Message Signal');  
  xlabel('Time (s)');  
  ylabel('Amplitude');  
  
  c = Ac * cos(2 * %pi * fc * t);  
  subplot(4,1,2);  
  plot(t, c);  
  title('Carrier Signal');  
  xlabel('Time (s)');  
  ylabel('Amplitude');   
  
  
  s1 = (Ac + m) .* cos(2 * %pi * fc * t);  
  s2 = (Ac - m) .* cos(2 * %pi * fc * t);  
  s  = s1 - s2;  
  subplot(4,1,3);  
  plot(t, s);  
  title('DSB-SC Modulated Signal');  
  xlabel('Time (s)');  
  ylabel('Amplitude');  
  
  
  demod_raw = s .* cos(2 * %pi * fc * t);  
  
  
  N = 100;  
  h = ones(1, N) / N;  
  demod = filter(h, 1, demod_raw);  
  delay = floor((N-1)/2);  
  demod = demod(delay+0.1:$);  
  t = t(1:length(demod));  
  
  
  demod = demod - mean(demod);  
  demod = demod / max(abs(demod)) * Am;  
  
  subplot(4,1,4);  
  plot(t, demod);  
  title('Demodulated Signal');  
  xlabel('Time (s)');  
  ylabel('Amplitude');  
TABULATION:
<img width="661" height="436" alt="Screenshot 2025-11-20 084722" src="https://github.com/user-attachments/assets/b942d79e-b3ab-4929-966a-aaf30cd0a4f6" />

OUTPUT:
<img width="608" height="505" alt="Screenshot 2025-11-20 084731" src="https://github.com/user-attachments/assets/80efcb26-ff26-4aac-9433-3619421f8c13" />

RESULT:
Thus, the DSB-SC-AM Modulation and Demodulation is generated.
