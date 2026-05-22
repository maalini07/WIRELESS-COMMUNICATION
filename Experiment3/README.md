# **Experiment 3: SNR Improvement Using Diversity Techniques**

## **Name** : MAALINI B N

## **Register Number** : 212224060136

## **Aim**
To analyze SNR improvement using diversity techniques in wireless communication using MATLAB.

## **Apparatus Required**
- MATLAB Software / GNU Octave
- Computer or Laptop
- Internet Connection

## **Procedure**
1. Initialize the MATLAB environment.
2. Generate random input signal samples.
3. Generate noise signals for different branches.
4. Create received signals with noise.
5. Calculate SNR before diversity.
6. Apply diversity combining technique.
7. Calculate SNR after diversity.
8. Plot the graph for SNR comparison.
9. Analyze the improvement in signal quality.

## **MATLAB Code**

```
clc;
clear all;
close all;

N = 1000;

signal = randn(1,N);

noise1 = 0.5 * randn(1,N);
noise2 = 0.5 * randn(1,N);

r1 = signal + noise1;
r2 = signal + noise2;

signal_power = mean(signal.^2);

noise_power1 = mean(noise1.^2);

SNR_before = 10 * log10(signal_power / noise_power1);

r_combined = (r1 + r2) / 2;

combined_noise = r_combined - signal;

noise_power_combined = mean(combined_noise.^2);

SNR_after = 10 * log10(signal_power / noise_power_combined);

fprintf('SNR Before Diversity = %.2f dB\n', SNR_before);

fprintf('SNR After Diversity  = %.2f dB\n', SNR_after);

fprintf('SNR Improvement      = %.2f dB\n', ...
        (SNR_after - SNR_before));

figure;

bar([SNR_before SNR_after]);

set(gca,'XTickLabel',{'Before Diversity','After Diversity'});

ylabel('SNR (dB)');

title('SNR Improvement Using Diversity Techniques');

grid on;
```

## **Output**
<img width="315" height="74" alt="image" src="https://github.com/user-attachments/assets/e763e642-9e99-431d-91f0-50ca6c7c20ed" />

<img width="678" height="528" alt="image" src="https://github.com/user-attachments/assets/917f8d16-f90d-4959-9d24-608304a18d9a" />

## **Result**
Thus the SNR improvement using diversity techniques was analyzed successfully using MATLAB.
