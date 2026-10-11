# Golay Radar Signal Target Detection [Attached MATLAB Code and Report]

Golay emitted signal target distance—Doppler blurred image
- Match filtering for distance estimation in both time and frequency domains - 2D distance for moving targets
- Doppler processing
- Repetitive practice with multiple targets (3)
- CFAR detection based on cell averaging for target parameters (amplitude, distance, and Doppler)
- Repetitive the above practice with Golay elastic sequences for Doppler
Method of sending and receiving signals
For the Golay transmitted signal, 512 samples of the Golay sequence were obtained in one PRI. Then, zero padding was performed to have a 50% duty cycle, thus generating 1024 samples in one PRI. For the received signal, the sent signal is shifted according to the sampling number corresponding to the time delay.
Distance Estimation
In the time domain: The estimated distance uses the xcorr function for time domain matching filtering.
In the frequency domain: We know that convolution in the time domain is equivalent to multiplication in the frequency domain. First, the received and transmitted signals are converted from the time domain to the frequency domain using the fast Fourier transform (FFT) function. Then, the received signal is multiplied by the conjugate of the transmitted signal. Finally, the IFFT function is used for the fast Fourier inverse transform.
Two-dimensional distance Doppler processing
For two-dimensional distance Doppler processing, the considered signal is a 2D array with M rows and N columns, in our case, M = 1024 and N = 2048. The column number N represents the number of PRI in one CPI, also known as slow time samples. The row number M represents the number of fast time samples in one PR.
Calculate distance delays and Doppler delays to construct the received signal. By shifting the signal according to the sample number corresponding to the time delay, distance delays are combined. By multiplying each column by ej 2 π·fd·xTpri, where fd is the Doppler frequency corresponding to the target speed and x denotes the column number from 0 to N-1, the Doppler delay is combined.
2D Doppler processing is performed by performing matching filtering across columns and Doppler processing across rows. The Doppler processing is carried out using Fast Fourier Transform (FFT). We know that for matching filtering, if the input parameters consist of n samples, then the output will have 2n-1 samples. We also know that for FFT, if the input parameters consist of n samples, then the output will have n samples. Therefore, the size of the 2D Doppler processed image is 2047 x 2048.
Multi-target two-dimensional Doppler
For 2D Doppler of multiple targets, we first fix the target distance and velocity, just like for three targets, we create two arrays for target distance and velocity. Then we loop until 1 to 3, and in each iteration, we find the 2D Doppler plot for each target, we add (superimpose) each 2D Doppler plot to a matrix initialized with the same dimensions and set to zero at the beginning. Finally, after the loop, we use imagesc to draw the superimposed 2D Doppler plots.
CFAR  
For CFAR, we first use the phase toolbox command to form a CFARDetector2D object with parameters training band size = [5,4], protection band size = [4,4], and false alarm probability of 1e-5. Now, in order to find the target points in the Doppler image, we must use the bands we defined to create cutting windows. To form the window, we loop over the start and end of rows and columns to attach all possible windows to the 2d array cutidx. Now, we use our created objects to use the created cuts to find the detection map. Afterwards, we draw the detection map using helperDetectionMaps from MATLAB to draw the detection map.
Golay sequence simulation results: emitting and receiving signals at a distance of 60 meters from the target.
\n Domain Matching Filter
\n        \n  
Domain Matching Filter
\n        \n  
Target two-dimensional Doppler for a target with a distance of 15 meters and a velocity of 50 meters/second.
\n        \n  
Target 2D Doppler (3)
For three targets, the distances are 10 meters, 20 meters and 30 meters, with speeds of 100 meters/second, 200 meters/second and 150 meters/second.
\n        \n  
FAR  
\n        \n  
Conclusions From the results of Golay sequences and Doppler elastic Golay sequences, the sidelobe ratio of Golay sequences is lower than that of Doppler elastic Golay sequences. This implies that Doppler elastic Golay sequences have a stronger main lobe, thus they are more accurate and have higher radar measurement resolution. Therefore, it indicates good performance. 
We have seen how to use 2D range-Doppler processing in radar signal processing for detecting moving targets in both range and velocity dimensions. Thus, it has applications in surveillance and target tracking radar systems. 
We also studied how to use CFAR (Constant False Alarm Rate) detection for further processing of range-Doppler maps to detect and track moving targets while minimizing false alarms by proposing appropriate thresholds. Overall, constant false alarm rate improves the performance of two-dimensional range-Doppler processing by reducing false alarms, increasing detection probability, and enhancing weak target detection in cluttered environments.

## Images

![Golay radar signal target detection [with MATLAB code and report]](01.png)
![Golay radar signal target detection [with MATLAB code and report]](02.png)
![Golay radar signal target detection [with MATLAB code and report]](03.png)
![Golay radar signal target detection [with MATLAB code and report]](04.png)
![Golay radar signal target detection [with MATLAB code and report]](05.png)
![Golay radar signal target detection [with MATLAB code and report]](06.png)
![Golay radar signal target detection [with MATLAB code and report]](07.png)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
