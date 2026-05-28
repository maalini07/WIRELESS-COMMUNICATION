# **Experiment 5: NFC Data Transmission Simulation**

## **Name** : MAALINI B N

## **Register Number** : 212224060136

## **Aim**
To simulate Near Field Communication (NFC) data transmission using MATLAB.

## **Apparatus Required**
- MATLAB Software / GNU Octave
- Computer or Laptop
- Internet Connection

## **Procedure**
1. Initialize the MATLAB environment.
2. Generate random binary data.
3. Apply ASK modulation for NFC transmission.
4. Generate carrier signal.
5. Add noise to the transmitted signal.
6. Perform signal demodulation at the receiver.
7. Recover the transmitted data.
8. Calculate Bit Error Rate (BER).
9. Plot original, modulated, and received signals.

## **MATLAB Code**

```
clc;
clear all;
close all;

N = 20;

data = randi([0 1],1,N);

disp('Transmitted Data:');
disp(data);

Tb = 1; 
fc = 10;
t = 0:0.01:Tb;

ask_signal = [];

for i = 1:N

    if data(i) == 1
        s = sin(2*pi*fc*t);
    else
        s = zeros(size(t));
    end

    ask_signal = [ask_signal s];
end

noise = 0.3 * randn(size(ask_signal));

received_signal = ask_signal + noise;

received_bits = [];

samples = length(t);

for i = 1:N

    segment = received_signal((i-1)*samples+1:i*samples);

    energy = sum(segment.^2);

    if energy > 5
        received_bits = [received_bits 1];
    else
        received_bits = [received_bits 0];
    end
end

BER = sum(data ~= received_bits)/N;

disp('Received Data:');
disp(received_bits);

fprintf('Bit Error Rate (BER) = %.4f\n', BER);

figure;

subplot(3,1,1);
stairs(data,'LineWidth',2);
title('Original Binary Data');
ylim([-0.5 1.5]);
grid on;

subplot(3,1,2);
plot(ask_signal,'LineWidth',1.5);
title('NFC ASK Modulated Signal');
grid on;

subplot(3,1,3);
plot(received_signal);
title('Received Signal with Noise');
grid on;
```

## **Output**

<img width="408" height="118" alt="image" src="https://github.com/user-attachments/assets/c359d711-ae6f-406e-8ad1-a78440fc3dba" />

<img width="989" height="790" alt="image" src="https://github.com/user-attachments/assets/55d6d8b1-2792-4558-8e34-a7036901af41" />

## **Result**
Thus the NFC data transmission was simulated successfully using MATLAB.
