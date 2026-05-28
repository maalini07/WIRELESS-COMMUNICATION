# **Experiment 4: BER Performance of Multiple Access Techniques**

## **Name** : MAALINI B N

## **Register Number** : 212224060136

## **Aim**
To simulate BER performance of multiple access techniques under noisy conditions using MATLAB.

## **Apparatus Required**
- MATLAB Software / GNU Octave
- Computer or Laptop
- Internet Connection

## **Procedure**
1. Initialize the MATLAB environment.
2. Generate random binary input data.
3. Apply BPSK modulation.
4. Define SNR range for simulation.
5. Simulate FDMA transmission under noisy conditions.
6. Simulate CDMA transmission using spreading code.
7. Calculate BER for FDMA and CDMA.
8. Plot BER versus SNR graph.
9. Compare the performance of multiple access techniques.

## **MATLAB Code**

```
clc;
clear all;
close all;

N = 10000;

data = randi([0 1],1,N);

bpsk_signal = 2*data - 1;

snr_db = 0:2:20;

BER_FDMA = zeros(size(snr_db));
BER_CDMA = zeros(size(snr_db));

code = [1 -1 1 -1];

for k = 1:length(snr_db)

    snr_linear = 10^(snr_db(k)/10);

    noise_std = sqrt(1/(2*snr_linear));

    noise = noise_std * randn(1,N);

    received_fdma = bpsk_signal + noise;

    detected_fdma = received_fdma > 0;

    BER_FDMA(k) = sum(data ~= detected_fdma)/N;

    spread_signal = kron(bpsk_signal, code);

    noise_cdma = noise_std * randn(1,length(spread_signal));

    received_cdma = spread_signal + noise_cdma;

    detected_cdma = zeros(1,N);

    for i = 1:N

        segment = received_cdma((i-1)*4+1:i*4);

        value = sum(segment .* code);

        if value > 0
            detected_cdma(i) = 1;
        else
            detected_cdma(i) = 0;
        end
    end

    BER_CDMA(k) = sum(data ~= detected_cdma)/N;

end

figure;

semilogy(snr_db,BER_FDMA,'r-o','LineWidth',2);
hold on;

semilogy(snr_db,BER_CDMA,'b-*','LineWidth',2);

grid on;

xlabel('SNR (dB)');
ylabel('Bit Error Rate (BER)');

title('BER Performance of Multiple Access Techniques');

legend('FDMA','CDMA');

disp('SNR(dB)   BER_FDMA      BER_CDMA');

for i = 1:length(snr_db)

    fprintf('%3d \t %e \t %e\n', ...
        snr_db(i), BER_FDMA(i), BER_CDMA(i));

end
```

## **Output**

<img width="392" height="268" alt="image" src="https://github.com/user-attachments/assets/5115e739-4607-4ccf-adb3-6019e142d15e" />

<img width="857" height="547" alt="image" src="https://github.com/user-attachments/assets/6a304f59-aae4-4b68-b048-5c64e70f1c14" />

## **Result**
Thus the BER performance of multiple access techniques under noisy conditions was simulated successfully using MATLAB.
