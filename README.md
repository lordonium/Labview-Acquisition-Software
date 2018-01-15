<p align="center"><img width=100% src="https://github.com/lordonium/Labview-Acquisition-Software/blob/master/media/main_pic.png"></p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
![LabVIEW](https://img.shields.io/badge/LabVIEW-v2015.1-yellow.svg)
![Dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg)
![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Basic Overview
Every experiment implies acquiring some measurement data, saving and analyzing it. While workinng at P.L. Kapitza Institute for Physical Problems of Russian Academy of Sciences I was asked to wrtite a software to perform afore mentioned tasks for several instruments:
 
* 6221 Keithley Precision DC and AC+DC Low Noise Current Source
* 2000 Keithley Precision Multimeter
* 5110 EG&G Princeton Applied Research Lock-In Amplifier
* KUSB-3116 Keithley 16-Bit USB DAQ Module

As a result I have written 9 Pre-Alpha versions, 6 Alpha versions and 3 Beta versions.

The current version is [Beta Ver 1.2.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Beta/Beta%20Ver%201.2.vi). 

## Details 

#### **Instruments**

Most of the instruments did not give any trouble while indtalling all the necessary libraries. Practically all of them had a support from National Instruments. However, Lock-In's libs were a little bit outdated, so I had to fix it by replacing the 'Visa open' function with the new one.

To our greatest fears the DAQ was ~~a pain in the ass~~. Not only did it have faulty drivers, it also got possesed by a demon. Actually, Keithley company was purchased by Tektronix and consequently they canceled the support for this product. As a result, the libs could only be installed only on the *LabVIEW 7.1*. After some magic was applied I found the manufacturing company who producers the original DAQ boards for other brands and got from their official website all the needed drivers and libs.

#### **Software**

Here I will explain the main parts in order for the users to speed up the compilation process.

1. **[Beta Ver 1.2.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Beta/Beta%20Ver%201.2.vi)**

This is the main VI which acquires data from our instruments writes it into the measurement file and also represents it in the real time plot figure. 

2. **[File creation.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Folder_file_subvi/folder_creation.vi)**

This subVI creates the measurement file in this pattern: *'hh_mm_ss.dat'*. It can be used in other projects.

3. **[Folder creation.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Folder_file_subvi/file_creation.vi)**

This subVI checks if the folder has already been created or creates one in this pattern: *'prename_dd_mm_yyyy'*.  It can be used in other projects too.

4. **[Instruments Readings.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/instr_comments_readings/com_inst.vi)**

This subVI outputs a string with initial instruments' settings that is futher written into the measurements file. As a part of the experiment the users need to know how the instruments were preconfigured.

5. **[Get Lock-In's sensitivity.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/instr_comments_readings/read_sense.vi)**

This subVI gets Lock-In's sensitivity.

6. **[Get Lock-In's time constant.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/instr_comments_readings/read_time_const.vi)**

This subVI gets Lock-In's Time Constant.

If by any chance you know Russian, you can read a very detailed explanation of the project in this report: [Report](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/media/report.pdf)

## Testing the Software without Preamps

Here is a demonstration of the working software without preamplifiers. 

[![](https://img.youtube.com/vi/1zslwP459LM/0.jpg)](https://www.youtube.com/watch?v=1zslwP459LM)

## Testing the Software with Preamps

Here is a demonstration of the working software with preamplifiers. 

[![](https://img.youtube.com/vi/ykHOAFcCeJ0/0.jpg)](https://www.youtube.com/watch?v=ykHOAFcCeJ0)

## Results

#### **The results of the measurement of the 1kOhm sample with preamplifiers**

```
# 1kOhm 08/12/2017  PREAMPS EXPERIMENT
# Lock-In: 5110 Sensitivity: 100mV Time Constant: MIN | | Keithley: 6221 Start current: 1.00E-6 A Stop current: 2.00E-6 A
# t, ms   6221, A      2000, V      5110_X, V      5110_Y, V    DAQ A0, V      DAQ A1, V    DAQ A2, V    DAQ A3, V     DAQ A4, V     
00000648   1.00E-6     0.998236     3.35000E-3    9.1000E-4   -9.0332E-1    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000610 
00001857   1.02E-6     1.016245     3.24000E-3    1.8300E-3   -9.6069E-1     6.1035E-4    0.0000E+0    -3.0518E-4      0.000000 
00002216   1.04E-6     1.037809     3.95000E-3    2.6800E-3   -9.9365E-1    -3.0518E-4    0.0000E+0    -3.0518E-4      0.000000 
00003000   1.06E-6     1.048590     3.28000E-3    2.1600E-3   -1.0294E+0    -6.1035E-4   -3.0518E-4    -3.0518E-4      0.000000 
00004000   1.08E-6     1.076034     3.24000E-3    2.1800E-3   -1.0544E+0    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000305 
00005000   1.10E-6     1.095850     3.21000E-3    1.6600E-3   -1.0739E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00006000   1.12E-6     1.115176     3.19000E-3    2.0600E-3   -1.0947E+0     0.0000E+0   -3.0518E-4     0.0000E+0     -0.000305 
00007000   1.14E-6     1.136197     3.42000E-3    2.1100E-3   -1.1148E+0     0.0000E+0   -3.0518E-4     3.0518E-4      0.000000 
00008000   1.16E-6     1.155186     3.49000E-3    2.2300E-3   -1.1346E+0     0.0000E+0    0.0000E+0    -3.0518E-4      0.000000 
00009000   1.18E-6     1.175308     3.57000E-3    2.6300E-3   -1.1545E+0    -6.1035E-4    0.0000E+0     0.0000E+0      0.000000 
00010000   1.20E-6     1.196291     4.00000E-3    6.7000E-4   -1.1749E+0     0.0000E+0   -6.1035E-4     0.0000E+0     -0.000305 
00011000   1.22E-6     1.197205     3.77000E-3    4.2000E-4   -1.1942E+0     0.0000E+0   -3.0518E-4     0.0000E+0      0.000000 
00012000   1.24E-6     1.236288     3.62000E-3    8.4000E-4   -1.2149E+0    -3.0518E-4   -6.1035E-4     0.0000E+0      0.000000 
00013000   1.26E-6     1.243644     3.56000E-3    6.8000E-4   -1.2344E+0     0.0000E+0   -6.1035E-4    -3.0518E-4     -0.000305 
00014000   1.28E-6     1.275445     3.46000E-3    4.7000E-4   -1.2537E+0    -6.1035E-4    3.0518E-4     0.0000E+0      0.000000 
00015000   1.30E-6     1.295473     3.34000E-3    8.1000E-4   -1.2747E+0     0.0000E+0    0.0000E+0    -6.1035E-4     -0.000610 
00016000   1.32E-6     1.316456     3.27000E-3    1.0800E-3   -1.2946E+0     3.0518E-4    0.0000E+0    -3.0518E-4     -0.000305 
00017000   1.34E-6     1.335293     3.28000E-3    1.1600E-3   -1.3147E+0     0.0000E+0   -6.1035E-4     0.0000E+0     -0.000305 
00018000   1.36E-6     1.356196     3.17000E-3    1.3600E-3   -1.3339E+0     0.0000E+0   -3.0518E-4     3.0518E-4     -0.000305 
00019000   1.38E-6     1.375481     3.19000E-3    2.0100E-3   -1.3538E+0     0.0000E+0    3.0518E-4    -3.0518E-4     -0.000305 
00020000   1.40E-6     1.395838     4.01000E-3    2.1300E-3   -1.3727E+0    -6.1035E-4   -3.0518E-4    -3.0518E-4     -0.000610 
00021000   1.42E-6     1.414718     3.98000E-3    2.4900E-3   -1.3943E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00022000   1.44E-6     1.435626     3.75000E-3    2.7700E-3   -1.4139E+0     0.0000E+0    0.0000E+0    -3.0518E-4      0.000000 
00023000   1.46E-6     1.454992     3.62000E-3    2.4700E-3   -1.4349E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4      0.000305 
00024000   1.48E-6     1.475668     3.55000E-3    2.5500E-3   -1.4542E+0     0.0000E+0   -6.1035E-4     0.0000E+0     -0.000305 
00025000   1.50E-6     1.495000     3.52000E-3    2.7600E-3   -1.4743E+0     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000305 
00026000   1.52E-6     1.515557     3.32000E-3    2.5200E-3   -1.4941E+0    -3.0518E-4    0.0000E+0     0.0000E+0      0.000000 
00027000   1.54E-6     1.534987     4.25000E-3    2.2000E-3   -1.5137E+0    -3.0518E-4   -3.0518E-4    -6.1035E-4     -0.000305 
00028000   1.56E-6     1.555247     4.23000E-3    2.1800E-3   -1.5338E+0    -3.0518E-4    0.0000E+0     0.0000E+0      0.000000 
00029000   1.58E-6     1.574216     4.28000E-3    1.8600E-3   -1.5533E+0    -3.0518E-4    0.0000E+0    -3.0518E-4      0.000000 
00030000   1.60E-6     1.582733     4.30000E-3    1.2500E-3   -1.5738E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00031000   1.62E-6     1.613834     4.12000E-3    1.1600E-3   -1.5933E+0     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000305 
00032000   1.64E-6     1.621248     4.03000E-3    9.6000E-4   -1.6135E+0    -3.0518E-4    0.0000E+0    -6.1035E-4      0.000000 
00033000   1.66E-6     1.654703     3.88000E-3    5.5000E-4   -1.6336E+0    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000305 
00034000   1.68E-6     1.668042     3.68000E-3    6.2000E-4   -1.6531E+0    -3.0518E-4   -6.1035E-4     0.0000E+0     -0.000305 
00035000   1.70E-6     1.694603     3.58000E-3    7.9000E-4   -1.6733E+0     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000305 
00036000   1.72E-6     1.702710     3.54000E-3    4.8000E-4   -1.6934E+0     0.0000E+0   -9.1553E-4    -3.0518E-4      0.000000 
00037000   1.74E-6     1.734313     3.38000E-3    2.7100E-3   -1.7136E+0     0.0000E+0    0.0000E+0    -3.0518E-4     -0.000610 
00038000   1.76E-6     1.744599     3.27000E-3    1.0700E-3   -1.7325E+0    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000305 
00039000   1.78E-6     1.773869     3.33000E-3    2.1700E-3   -1.7529E+0    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000305 
00040000   1.80E-6     1.779540     3.21000E-3    2.0300E-3   -1.7722E+0     0.0000E+0    0.0000E+0    -3.0518E-4     -0.000305 
00041000   1.82E-6     1.812543     3.21000E-3    1.3200E-3   -1.7935E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4      0.000000 
00042000   1.84E-6     1.829009     3.33000E-3    1.2000E-3   -1.8130E+0     0.0000E+0    0.0000E+0     0.0000E+0      0.000000 
00043000   1.86E-6     1.852889     3.48000E-3    1.1600E-3   -1.8329E+0    -3.0518E-4    0.0000E+0     0.0000E+0     -0.000305 
00044000   1.88E-6     1.872276     3.54000E-3    8.1000E-4   -1.8527E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4      0.000000 
00045000   1.90E-6     1.893485     3.71000E-3    5.6000E-4   -1.8732E+0     0.0000E+0    3.0518E-4     0.0000E+0      0.000000 
00046000   1.92E-6     1.911982     3.89000E-3    6.4000E-4   -1.8927E+0    -3.0518E-4    3.0518E-4    -3.0518E-4     -0.000610 
00047000   1.94E-6     1.931789     3.98000E-3    8.3000E-4   -1.9128E+0     3.0518E-4   -3.0518E-4     3.0518E-4     -0.000610 
00048000   1.96E-6     1.953195     3.98000E-3    5.5000E-4   -1.9327E+0    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000610 
00049000   1.98E-6     1.972151     4.15000E-3    4.9000E-4   -1.9528E+0    -3.0518E-4    0.0000E+0    -3.0518E-4      0.000000 
00050000   2.00E-6     1.993207     4.28000E-3    1.0700E-3   -1.9730E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4      0.000000 
```

#### **Another example of the measurement file in which case the Lock-In's sensitivity was changed**
```
# 16/11/17
# Lock-In: 5110 Sensitivity: 500mV Time Constant: MIN | | Keithley: 6221 Start current: 1.00E-3 A Stop current: 1.20E-3 A
# t, ms   6221, A      2000, V      5110_X, V      5110_Y, V    DAQ A0, V      DAQ A1, V    DAQ A2, V    DAQ A3, V     DAQ A4, V     
00000664   1.00E-3     0.999635     2.30000E-2    3.0000E-4    9.9945E-1     0.0000E+0   -6.1035E-4     0.0000E+0     -0.000305 
00001862   1.00E-3     1.003631     1.88500E-2    9.6000E-3    1.0037E+0     0.0000E+0    0.0000E+0    -3.0518E-4      0.000000 
00002267   1.01E-3     1.007625     2.01500E-2    3.6000E-3    1.0083E+0    -6.1035E-4    0.0000E+0    -3.0518E-4      0.000000 
00002995   1.01E-3     1.011620     1.56000E-2    1.3900E-2    1.0110E+0    -3.0518E-4    0.0000E+0     0.0000E+0      0.000000 
00003995   1.02E-3     1.015577     2.14500E-2    7.9500E-3    1.0165E+0    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000610 
00004995   1.02E-3     1.019607     1.87500E-2    8.4000E-3    1.0196E+0    -3.0518E-4   -3.0518E-4     0.0000E+0      0.000000 
00005995   1.02E-3     1.023602     1.88500E-2    6.8000E-3    1.0242E+0    -3.0518E-4    0.0000E+0     0.0000E+0      0.000000 
00006995   1.03E-3     1.027670     1.87500E-2    8.6000E-3    1.0269E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00007995   1.03E-3     1.031628     1.84000E-2    8.8000E-3    1.0278E+0     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000305 
00008995   1.04E-3     1.035662     1.89000E-2    8.6000E-3    1.0355E+0     0.0000E+0    0.0000E+0     3.0518E-4      0.000000 
# Sensitivity: 100mV
00009995   1.04E-3     1.039618    -6.20000E-4   -2.3400E-3    1.0394E+0    -6.1035E-4   -3.0518E-4     0.0000E+0      0.000000 
00010995   1.04E-3     1.043662     2.68000E-3    2.1200E-3    1.0437E+0    -3.0518E-4   -3.0518E-4    -6.1035E-4      0.000000 
00011995   1.05E-3     1.047620     1.51000E-3   -1.3900E-3    1.0464E+0    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00012995   1.05E-3     1.051651     3.72000E-3    1.7600E-3    1.0519E+0    -3.0518E-4    3.0518E-4     0.0000E+0      0.000000 
00013995   1.06E-3     1.055608     3.79000E-3    1.7100E-3    1.0550E+0    -6.1035E-4    0.0000E+0    -3.0518E-4      0.000000 
00014995   1.06E-3     1.059641     2.89000E-3   -2.0000E-5    1.0587E+0     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000610 
00015995   1.06E-3     1.063635     4.79000E-3    3.3600E-3    1.0635E+0    -3.0518E-4    0.0000E+0    -6.1035E-4      0.000000 
00016995   1.07E-3     1.067631     3.75000E-3    1.7300E-3    1.0675E+0    -3.0518E-4   -9.1553E-4    -3.0518E-4     -0.000305 
00017995   1.07E-3     1.071624     3.79000E-3    1.9200E-3    1.0712E+0    -3.0518E-4   -6.1035E-4     0.0000E+0      0.000305 
```
## Authors

* **Sergey Chernayev** - *Initial work* - [lordonium](https://github.com/lordonium)

All other known bugs and fixes can be sent to chernayev.sergey.work@gmail.com

Reported bugs/fixes will be submitted to correction
<!-- See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.
 -->
## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* [Arutyunov Konstantin Yurievich](https://www.hse.ru/en/org/persons/117711945) (for an exciting opportunity to work on this amazing project)
* [Zavyalov Vitaly Vadimovich](http://www.kapitza.ras.ru/~zav/index.en.php) (inspiring ideas about DAQ and software in general)
* Khaldeev Stanislav Igorevich (amazing tips about the code) 

