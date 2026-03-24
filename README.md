# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 
```
clc;
clear;
close;

disp("Loading audio files...");

// Read reference and test voice files
[y1, fs1] = wavread("C:\Users\public\Downloads\referance.wav");
[y2, fs2] = wavread("C:\Users\public\Downloads\test.wav");

// Check sampling rates
if fs1 <> fs2 then
    error("Sampling rates must match!");
end

// Convert stereo to mono (if needed)
if size(y1,2) == 2 then
    y1 = mean(y1, 2);
end
if size(y2,2) == 2 then
    y2 = mean(y2, 2);
end

// Make both signals same length
n = min(length(y1), length(y2));
y1 = y1(1:n);
y2 = y2(1:n);

// Compute Euclidean distance
dist = sqrt(sum((y1 - y2).^2));

disp("Euclidean distance (reference vs test): " + string(dist));

// Decision based on threshold
if dist < 0.5 then
    disp("Matching with reference (same word)");
else
    disp("Not matching with reference (different word)");
end

// Plot both signals
figure(0);
subplot(2,1,1);
plot(y1);
title("REFERENCE VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

subplot(2,1,2);
plot(y2);
title("TEST VOICE SIGNAL");
xlabel("Samples");
ylabel("Amplitude");

// Comparison plot
figure(1);
plot(y1, 'b');
plot(y2, 'r');
title("Reference (Blue) vs Test (Red) Signal");
xlabel("Samples");
ylabel("Amplitude");
legend(["Reference", "Test"]);

disp("Waveforms plotted successfully.");
```

## OUTPUT: 

<img width="1559" height="941" alt="image" src="https://github.com/user-attachments/assets/7964f5b3-5fd9-4ef6-b934-024963a49095" />

<img width="1565" height="870" alt="image" src="https://github.com/user-attachments/assets/bc346422-e8d8-4e5c-acf9-81f10a8c0f4e" />

## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
