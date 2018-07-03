# IND3156

Fast Fourier Transform in fortran

A fast Fourier transform (FFT) is an algorithm that calculates the discrete Fourier transform (frequency components) of some sequence – the discrete Fourier transform transforms the structure of the cycle of a waveform into sine components. A FFT can be used in various types of signal processing. It may be useful in reading things like sound waves, or for any image-processing technologies. A fast Fourier transform can be used to solve various types of equations, or show various types of frequency activity in useful ways.

I found a code online that I'll tweak but first I'm going to select the most important lines of code and explain what they mean.


ONLINE CODE

implicit real*8 (a-h,o-z)
  all variables with names beginning with either letter of 'a' to 'h' and 'o' to 'z' are declared real with size 8

character*12 if,of
  


