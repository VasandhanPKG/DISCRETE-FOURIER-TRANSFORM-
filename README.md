# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# REG NO : 212223060122

##  AIM: 
To Obtain DFT and FFT of a given sequence in SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM: 
**DISCRETE FOURIER TRANSFORM-DIRECT**
```python
clc;
clear;

xn = input("Enter the sequence in square brackets [ ] : ");

n1 = 0:1:length(xn)-1;


subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

j = %i;
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp((-j*2*%pi*k*n)/N);
    end
end

disp("DFT Values (Xk):");
for k = 1:N
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < N then
        printf(" , ");
    else
        printf("\n");
    end
end

K1 = 0:1:length(Xk)-1;

magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

angle = atan(imag(Xk), real(Xk));
subplot(3,1,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');

```
**DFT USING FFT**
```python
clc;
clear;
close;

// User input
xn = input("Enter the sequence in square brackets [ ] : ");   // Example: [1 2 3 4 4 3 2 1]

// Index for input
n1 = 0:1:length(xn)-1;

// Plot input sequence
subplot(2,2,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude');
title('Input Sequence');

// FFT calculation
Xk = fft(xn);

// Display formatted FFT values
disp("FFT Values (Xk):");
for k = 1:length(Xk)
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));   // purely real
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < length(Xk) then
        printf(" , ");
    else
        printf("\n");
    end
end

// Frequency index
K1 = 0:1:length(Xk)-1;

// Magnitude Spectrum
magnitude = abs(Xk);
subplot(2,2,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

// Phase Spectrum
angle = atan(imag(Xk), real(Xk));
subplot(2,2,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');

// IFFT (reconstructed signal)
y = ifft(Xk);
n2 = 0:1:length(y)-1;
subplot(2,2,4);
plot2d3(n2, y);
xlabel('Time n');
ylabel('Amplitude');
title('Inverse FFT of X(k)');

```

## OUTPUT:

## **DIRECT**

<img width="764" height="720" alt="Screenshot 2025-10-16 133418" src="https://github.com/user-attachments/assets/1fda2a0f-d0a2-4a47-81c5-15b59dae9d37" />

## **DFT USING FFT**

<img width="761" height="719" alt="Screenshot 2025-10-16 133444" src="https://github.com/user-attachments/assets/cdca0f1b-cca2-422a-93b8-61b9f6dae694" />


## RESULT: 
Thus, the Discrete Fourier Transform and Fast Fourier Transform of the given sequence were obtained and its magnitude and phase spectrum were plotted.
