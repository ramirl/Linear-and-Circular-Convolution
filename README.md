# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
// Linear Convolution
clc; clear;
x = input("Enter x(n) as a row vector: ");   // e.g., [1 1 2 1]
h = input("Enter h(n) as a row vector: ");   // e.g., [1 2 3 4]

Nx = length(x); 
Nh = length(h);
Ny = Nx + Nh - 1; 
y = zeros(1, Ny);

// Linear convolution calculation
for n = 1:Ny
    acc = 0;
    for k = 1:Nx
        m = n - k + 1;
        if (m >= 1 & m <= Nh) then
            acc = acc + x(k) * h(m);
        end
    end
    y(n) = acc;
end

disp(y, "Linear convolution y =");

// Plot input and output sequences
subplot(3,1,1);
plot2d3(0:Nx-1, x);   // stem plot for x(n)
xtitle("Input sequence x(n)");

subplot(3,1,2);
plot2d3(0:Nh-1, h);   // stem plot for h(n)
xtitle("Impulse response h(n)");

subplot(3,1,3);
plot2d3(0:Ny-1, y);   // stem plot for convolution
xtitle("Linear Convolution y(n) = x(n) * h(n)");
```
## PROGRAM (Circular Convolution): 
```
// Circular Convolution
clc; clear;

// Input sequences
x1 = input("Enter the first sequence x1: "); // e.g., [1 2 3]
x2 = input("Enter the second sequence x2: "); // e.g., [4 5 6]

// Make both sequences equal length by zero-padding
N = max(length(x1), length(x2));
x1 = [x1, zeros(1, N-length(x1))];
x2 = [x2, zeros(1, N-length(x2))];

// Compute DFTs
X1 = fft(x1, -1);
X2 = fft(x2, -1);

// Multiply in frequency domain
Y = X1 .* X2;

// Compute IDFT to get circular convolution
y_circ = fft(Y, 1); // IDFT
y_circ = real(y_circ); // Take real part

disp(y_circ, "Circular Convolution y(n) =");

// Plot input and output sequences using stem-style plots
scf(1); // Figure 1
subplot(3,1,1);
xpoly(0:N-1, x1, 0, 1);
xtitle("Input sequence x1(n)");

subplot(3,1,2);
xpoly(0:N-1, x2, 0, 1);
xtitle("Input sequence x2(n)");

subplot(3,1,3);
xpoly(0:N-1, y_circ, 0, 1);
xtitle("Circular Convolution y(n)");
```

## OUTPUT (Linear Convolution): 
![WhatsApp Image 2025-09-08 at 15 17 39_21bd9f19](https://github.com/user-attachments/assets/c42864a6-aeda-4ffa-be31-1edcb7b95086)

## OUTPUT (Circular Convolution): 
![WhatsApp Image 2025-09-08 at 15 07 12_51524167](https://github.com/user-attachments/assets/f72003d5-4abe-454e-992c-b0cb159f5683)

## RESULT: 
Linear and Circular Convolution for two given sequence using SCILAB was performed.
