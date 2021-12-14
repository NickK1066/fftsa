# fftsa
FFT Spectrum Analyser

fftsa is my developing fast audio spectrum analyser focusing on the tools for DIY audio amp design and build.

The initial design is to support a 24bit 1MSPS ADC with a programmable filter for acquistiion. Multiple devices for processing samples and then displaying the information via a fast GUI interface using Vulkan/OpenGL. The idea is for a box on the bench, the same size roughly as a modern DSO.

Rough target feature list:
* Single channel programmable ADC provides decimation, filtering and sample ranges up to 1024 KSPS.
* Lossless sample acqisition using external clock to drive ADC and ensuring low jitter sample interval source, an RT OS for capture prevents latency (acquisiton on different hardware to display).
* Configurable sample history 
* Offline FFT processing with parallel decomposition across hardware, resolution up to sample rate (1Mpts at 1MSPS) using vkFFT.
* Realtime FFT processing for small FFT, for example 1024 bins allowing trigget history markers and snapshots using coefficient deltas.
* FFT in 'realtime' (my touch screen has a 100Hz response time) using Vulkan/OpenGL
  * Zoom and scroll - centre line, resolution span.
  * Harmonics peak identifiation / Nth highest peaks, THD, SNR
  * Configurable sample averanging
  * Configurable windowing
  * Find Frequncy Spike button. The FFS button is equivilent to the auto-setup on a digital osciloscope. 
* FFT Spectragram history
  * oscilation detection using FFT of the FFT in the time domain.
* Full frequency Bode plot 
* Store and retrieve samples

Given the processing challenge of 1MSPS with a 1Mpt FFT, the approach scales in processing across cores and hardware platforms.

Dependencies
* ImGUI
* vkFFT
