# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 

  To analyze audio signal by removing unwanted frequency. 

# APPARATUS REQUIRED: 
   
   PC installed with SCILAB/Python. 

# PROGRAM: 
```
clc;
clear;
clf();

[y, Fs] = wavread("C:\Users\acer\Downloads\reference.wav");

if size(y,2) == 2 then
    y = mean(y,2);
end

y = y / max(abs(y));

N = length(y);
t = (0:N-1)/Fs;

// FORCE COLUMN
t = t(:);
y = y(:);


figure(1);
plot(t, y);
xlabel('Time (seconds)');
ylabel('Amplitude');
title('Original Audio Signal');


Y = fft(y);
magnitude = abs(Y);
freq = (0:N-1)*(Fs/N);

freq = freq(:);
magnitude = magnitude(:);

halfN = floor(N/2);

figure(2);
plot(freq(1:halfN), magnitude(1:halfN));
xlabel('Frequency (Hz)');
ylabel('Magnitude');
title('Frequency Spectrum');


fc = 1000;

Yf = Y;

for i = 1:N
    if freq(i) > fc then
        Yf(i) = 0;
    end
end

y_filtered = real(ifft(Yf));
y_filtered = y_filtered(:);

figure(3);
plot(t, y_filtered);
xlabel('Time (seconds)');
ylabel('Amplitude');
title('Filtered Signal');

```

# OUTPUT: 
<img width="750" height="350" alt="image" src="https://github.com/user-attachments/assets/c3c27d39-db8b-4a63-b923-a08c6d2bae4e" />
<img width="750" height="350" alt="image" src="https://github.com/user-attachments/assets/bafd4655-d5b0-471f-9fef-87063d0a0dd2" />
<img width="750" height="350" alt="image" src="https://github.com/user-attachments/assets/b8045277-f1ba-4acc-b899-4ff848e3f55a" />




# RESULTS
Hence ANALYSIS OF DFT WITH AUDIO SIGNAL is done successfully..

