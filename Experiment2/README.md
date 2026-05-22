# **Experiment 2: Fade Margin Estimation in Wireless Links**

## **Name** : MAALINI B N

## **Register Number** : 212224060136

## **Aim**
To estimate fade margin in wireless communication links using MATLAB.

## **Apparatus Required**
- MATLAB Software / GNU Octave
- Computer or Laptop
- Internet Connection

## **Procedure**
1. Initialize the MATLAB environment.
2. Define transmitted power and antenna gains.
3. Set path loss and receiver sensitivity values.
4. Calculate received power.
5. Estimate fade margin.
6. Analyze link reliability.
7. Plot the graph for received power and fade margin.
8. Observe the wireless link performance.

## **MATLAB Code**

```
clc;
clear all;
close all;

Pt = 30;         
Gt = 15;          
Gr = 15;          
L = 120;        
Pr_min = -80;    
Pr = Pt + Gt + Gr - L;

Fade_Margin = Pr - Pr_min;

fprintf('Received Power = %.2f dBm\n', Pr);
fprintf('Receiver Sensitivity = %.2f dBm\n', Pr_min);
fprintf('Fade Margin = %.2f dB\n', Fade_Margin);

if Fade_Margin > 20
    disp('Excellent Link Reliability');
elseif Fade_Margin > 10
    disp('Good Link Reliability');
else
    disp('Poor Link Reliability');
end

figure;

bar([Pr Fade_Margin]);

set(gca,'XTickLabel',{'Received Power','Fade Margin'});

ylabel('Value in dB');

title('Fade Margin Estimation in Wireless Link');

grid on;
```

## **Output**
<img width="322" height="89" alt="image" src="https://github.com/user-attachments/assets/cc4164f6-cb08-4eca-9839-b6766493c58f" />

<img width="698" height="528" alt="image" src="https://github.com/user-attachments/assets/8aa81ff6-0076-4d35-94a0-9edcfd54f796" />

## **Result**
Thus the fade margin in wireless communication links was estimated successfully using MATLAB.
