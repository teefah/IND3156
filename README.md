# IND3156

Fast Fourier Transform in fortran

A fast Fourier transform (FFT) is an algorithm that calculates the discrete Fourier transform (frequency components) of some sequence. The discrete Fourier transform transforms the structure of the cycle of a waveform into sine components. A FFT can be used in various types of signal processing. It may be useful in reading things like sound waves, or for any image-processing technologies. A fast Fourier transform can be used to solve various types of equations, or show various types of frequency activity in useful ways. Go to http://www.aip.de/groups/soe/local/numres/bookfpdf/f12-2.pdf for further details.

-------------------------------------------------------------------------------------
Errors
-------------------------------------------------------------------------------------
I found a code online at http://www.physics.purdue.edu/~hisao/book/www/examples/appC/fft.f This code will give you a bunch of errors just because in the subroutine calc, they forgot to close the arithmetical if statement ```if(idir.eq.2) th=-th``` with ```endif``` after line 142. Fixing that one mistake will get rid of the 23 errors below.

```quest@stretch3B:~/mfl/project $ gfortran fourier.f
fourier.f:144:72:

 10      continue
                                                                        1
Error: End of nonblock DO statement at (1) is within another block
fourier.f:146:11:

         end
           1
Error: END IF statement expected at (1)
fourier.f:150:8:

         subroutine prep(data,nbit,ndata)
        1
Error: Unclassifiable statement at (1)
fourier.f:151:72:

         implicit real*8 (a-h,o-z)
                                                                        1
Error: Letter ‘A’ already has an IMPLICIT type at (1)
fourier.f:152:22:

         dimension data(1)
                      1
Error: Duplicate DIMENSION attribute specified at (1)
fourier.f:153:20:

fourier.f:118:72:

         do 10 i=1,nbit
                                                                        2
fourier.f:153:20:

         do 10 i=1,30
                    1
Error: Variable ‘i’ at (1) cannot be redefined inside loop beginning at (2)
fourier.f:143:2:

 20              continue
  1
fourier.f:161:2:

 20                      continue
  2
Error: Duplicate statement label 20 at (1) and (2)
fourier.f:144:2:

 10      continue
  1
fourier.f:164:2:

 10      continue
  2
Error: Duplicate statement label 10 at (1) and (2)
fourier.f:164:72:

 10      continue
                                                                        1
Error: End of nonblock DO statement at (1) is within another block
fourier.f:139:2:

 30                      continue
  1
fourier.f:165:2:

 30      ndata=n
  2
Error: Duplicate statement label 30 at (1) and (2)
fourier.f:167:11:

         end
           1
Error: END IF statement expected at (1)
fourier.f:171:8:

         function nrev(i,nbit)
        1
Error: Unclassifiable statement at (1)
fourier.f:144:2:

 10      continue
  1
fourier.f:177:2:

 10      continue
  2
Error: Duplicate statement label 10 at (1) and (2)
fourier.f:177:72:

 10      continue
                                                                        1
Error: End of nonblock DO statement at (1) is within another block
fourier.f:180:11:

         end
           1
Error: END IF statement expected at (1)
fourier.f:184:8:

         subroutine swap(data,nbit)
        1
Error: Unclassifiable statement at (1)
fourier.f:185:72:

         implicit real*8 (a-h,o-z)
                                                                        1
Error: Letter ‘A’ already has an IMPLICIT type at (1)
fourier.f:186:22:

         dimension data(1)
                      1
Error: Duplicate DIMENSION attribute specified at (1)
fourier.f:188:72:

fourier.f:118:72:

         do 10 i=1,nbit
                                                                        2
fourier.f:188:72:

         do 10 i=1,n
                                                                        1
Error: Variable ‘i’ at (1) cannot be redefined inside loop beginning at (2)
fourier.f:189:16:

                 m=nrev(i,nbit)
                1
Error: Unclassifiable statement at (1)
fourier.f:144:2:

 10      continue
  1
fourier.f:200:2:

 10      continue
  2
Error: Duplicate statement label 10 at (1) and (2)
fourier.f:200:72:

 10      continue
                                                                        1
Error: End of nonblock DO statement at (1) is within another block
fourier.f:202:11:

         end
           1
Error: END IF statement expected at (1)
f951: Error: Unexpected end of file in ‘fourier.f’
```


When you run it, it will ask  whether your data are real or imaginary numbers as expected. This corresponds to 1 and 2 respectively. Then it will ask ```input file name```. Obviously I need data so I imported one in Excel (fft.xlsx) and scp it to this project directory on the stretch3b. When I answered 'fft.xlsx' as the input file name, I get an error:

```
FFT forward (of real function) <1> or backward <2>?
1
input file name?
fft.xlsx
At line 59 of file fourier.f (unit = 1, file = 'fft.xlsx')
Fortran runtime error: Bad real number in item 1 of list input 
```

The code doesn't take Excel files. The data needs to be in plain text with 2 columns:time and space. putting ```write(6,*) t,data(j) ``` after line 54 in the subroutine input helps verify if the file actually gets open and read. The trick is to only have the spacial data (not temporal) in a column in plain text. When you do, the code will get executed.






```implicit real*8 (a-h,o-z)```
  all variables with names beginning with either letter of 'a' to 'h' and 'o' to 'z' are declared real (double precision) with size 8 bytes

```character*12 if,of``` if and of are strings of 12 characters. if points at the input data and of at the output.

There are 5 subroutines (input, prep, swap, calc, output) and 1 function (nrev).

Data are passed to the input subroutine and copied to ```if```. The REWIND statement is to reposition at the beginning of the file for the next READ or WRITE.
dcos and dsin are just old form of COS() and SIN() in fortran.

Not sure if this is actually computing my data right. I'm not confident about the format of the data but the code is being executed. The 2 attached picutes are graphical representation of the 1st 7 points.

  


