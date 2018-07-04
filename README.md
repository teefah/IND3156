# IND3156

Fast Fourier Transform in fortran

A fast Fourier transform (FFT) is an algorithm that calculates the discrete Fourier transform (frequency components) of some sequence. The discrete Fourier transform transforms the structure of the cycle of a waveform into sine components. A FFT can be used in various types of signal processing. It may be useful in reading things like sound waves, or for any image-processing technologies. A fast Fourier transform can be used to solve various types of equations, or show various types of frequency activity in useful ways. Go to [...] for further details.

-------------------------------------------------------------------------------------
Errors
-------------------------------------------------------------------------------------
I found a code online at http://www.physics.purdue.edu/~hisao/book/www/examples/appC/fft.f This code will give you a bunch of errors just because in the subroutine calc, they forgot to close the arithmetical if statement ```if(idir.eq.2) th=-th``` with ```endif``` between line [...] and line [...]. Fixing that one mistake will get rid of the 23 errors. 

When you run it, it will ask  whether your data is real or imaginary as expected. This corresponds to 1 and 2 respectively. Then it will ask ```input file name```. Obviously I need data so I created one in Excel (fft.xlsx) and scp it to this project directory on the stretch3b. When I answered 'fft.xlsx' as the input file name, I get an error:

```
FFT forward (of real function) <1> or backward <2>?
1
input file name?
fft.xlsx
At line 59 of file fourier.f (unit = 1, file = 'fft.xlsx')
Fortran runtime error: Bad real number in item 1 of list input 
```






----------------------------------------------------------------------------------------------------------------------------
Code
----------------------------------------------------------------------------------------------------------------------------

Below you'll find the relevant lines of the modified code and explain what they each mean. Then, I'll modify it to [...]


```implicit real*8 (a-h,o-z)```
  all variables with names beginning with either letter of 'a' to 'h' and 'o' to 'z' are declared real with size 8

```character*12 if,of```
  


