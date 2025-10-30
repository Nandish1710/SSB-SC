# SSB

EXP NO: 3	SSB-SC-AM MODULATION using SCILAB

AIM:

To write a program to perform SSBSC modulation and demodulation using SCI LAB and study its spectral characteristics

EQUIPMENTS REQUIRED

•	Computer with i3 Processor

•	SCI LAB

Note: Keep all the switch faults in off position


Algorithm
1.	Define Parameters:
•	Fs: Sampling frequency.
•	T: Duration of the signal.
•	Fc: Carrier frequency.
•	Fm: Frequency of the message signal.
•	Amplitude: Maximum amplitude of the message signal.
2.	Generate Signals:
•	Message Signal: The baseband signal that will be modulated.
•	Carrier Signal: A high-frequency signal used for modulation.
•	Analytic Signal: Constructed using the Hilbert transform to get the in-phase and quadrature components.
3.	SSBSC Modulation:
•	Modulated Signal: Create the SSBSC signal using the in-phase and quadrature components, modulated by the carrier.
4.	SSBSC Demodulation:
•	Mixing: Multiply the SSBSC signal with the carrier to retrieve the message signal.
•	Low-pass Filtering: Apply a low-pass filter to remove high-frequency components and recover the original message signal.
5.	Visualization:
•	Plot the message signal, carrier signal, SSBSC modulated signal, and the recovered signal after demodulation.


PROCEDURE

•	Refer Algorithms and write code for the experiment.
•	Open SCILAB in System
•	Type your code in New Editor
•	Save the file
 
•	Execute the code
•	If any Error, correct it in code and execute again
•	Verify the generated waveform using Tabulation and Model Waveform

Model Waveform

<img width="704" height="178" alt="image" src="https://github.com/user-attachments/assets/32ee29b3-0d95-4192-9762-972d50c05c90" />
<img width="706" height="167" alt="image" src="https://github.com/user-attachments/assets/bff0d8fd-d679-444e-af37-0b34585853c1" />

Program
clc;
clear;
close;
Am = 10.8;          // Message amplitude
Ac = 21.6;          // Carrier amplitude
Fm = 560;           // Message frequency (Hz)
Fc = 5600;          // Carrier frequency (Hz)
Fs = 55000;         // Sampling frequency (Hz)

//// Time vector
t = 0:1/Fs:0.005;   // 5 ms duration

//// Message signal
m = Am * sin(2 * %pi * Fm * t);

//// Carrier signal
c = Ac * sin(2 * %pi * Fc * t);

//// Hilbert transform (to get quadrature component)
mh = imag(hilbert(m));   // Hilbert transform of message

//// Generate Upper Sideband (USB)
s_usb = Ac * (m .* cos(2 * %pi * Fc * t) - mh .* sin(2 * %pi * Fc * t));
s_lsb = Ac * (m .* cos(2 * %pi * Fc * t) + mh .* sin(2 * %pi * Fc * t));
subplot(4,1,1)
plot(t, m)
title('Message Signal')
xlabel('Time (s)')
ylabel('Amplitude')
xgrid()

subplot(4,1,2)
plot(t, c)
title('Carrier Signal')
xlabel('Time (s)')
ylabel('Amplitude')
xgrid()

subplot(4,1,3)
plot(t, s_usb)
title('SSB-SC Upper Sideband Signal')
xlabel('Time (s)')
ylabel('Amplitude')
xgrid()

subplot(4,1,4)
plot(t, s_lsb)
title('SSB-SC Lower Sideband Signal')
xlabel('Time (s)')
ylabel('Amplitude')
xgrid()
disp("   Time(s)        Message(V)        Carrier(V)        USB(V)        LSB(V)");
for i = 1:10:length(t)
    mprintf("%10.6f    %10.4f    %10.4f    %10.4f    %10.4f\n", t(i), m(i), c(i), s_usb(i), s_lsb(i));
end

OUTPUT WAVEFORM
<img width="764" height="723" alt="Screenshot 2025-10-30 092248" src="https://github.com/user-attachments/assets/122e897a-0d28-475f-8715-62e09e23d03a" />



TABULATION
<img width="1280" height="767" alt="image" src="https://github.com/user-attachments/assets/0db73aac-164d-463b-a453-7436f0b7e1b7" />
RESULT:

Thus, the SSB-SC-AM Modulation and Demodulation is experimentally done and the output is verified.





