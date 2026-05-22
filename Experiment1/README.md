# **Experiment 1: Analysis of Power Control Techniques**

## **Name** : MAALINI B N

## **Register Number** : 212224060136

## **Aim**
To analyze Open Loop and Closed Loop Power Control techniques in wireless communication using MATLAB.

## **Apparatus Required**
- MATLAB Software / GNU Octave
- Computer or Laptop
- Internet Connection

## **Procedure**
1. Initialize the MATLAB environment.
2. Define distance between users and base station.
3. Set transmitted power and path loss exponent.
4. Calculate Open Loop received power.
5. Calculate Closed Loop received power.
6. Display calculated values.
7. Plot the graph for comparison.
8. Analyze the performance of both techniques.

## **MATLAB Code**

```
clc;
clear all;
close all;

n = 10;

d = linspace(0.5,5,n);

alpha = 3;

Pt = 1;

Pr_open = Pt ./ (d.^alpha);

target_power = 0.05;

Pr_closed = zeros(1,n);

for i = 1:n
    
    Pt_adjusted = target_power * (d(i)^alpha);
    
    Pr_closed(i) = Pt_adjusted / (d(i)^alpha);
end

fprintf('Distance (km)    Open Loop Power    Closed Loop Power\n');

for i = 1:n
    
    fprintf('%6.2f \t\t %8.4f \t\t %8.4f\n', ...
        d(i), Pr_open(i), Pr_closed(i));
end

figure;

plot(d,Pr_open,'r-o','LineWidth',2);
hold on;

plot(d,Pr_closed,'b-*','LineWidth',2);

grid on;

xlabel('Distance from Base Station (km)');
ylabel('Received Power');

title('Analysis of Power Control Techniques');

legend('Open Loop Power Control', ...
       'Closed Loop Power Control');
```

## **Output**
<img width="532" height="239" alt="image" src="https://github.com/user-attachments/assets/b364daae-8d64-4d0c-8539-51fa04360f61" />

<img width="554" height="455" alt="image" src="https://github.com/user-attachments/assets/c447cdc5-2ded-4a16-b234-208e040923ad" />

## **Result**
Thus the Open Loop and Closed Loop Power Control techniques were analyzed successfully using MATLAB.
