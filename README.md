<p align="center"><img width=100% src="https://github.com/lordonium/Labview-Acquisition-Software/blob/master/media/main_pic.png"></p>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
![LabVIEW](https://img.shields.io/badge/LabVIEW-v2015.1-yellow.svg)
![Dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg)
![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Basic Overview
Every experiment implies acquiring some measurement data, saving  and analyzing it. While workinng at P.L. Kapitza Institute for Physical Problems of Russian Academy of Sciences I was asked to wrtite a software to perform afore mentioned tasks for several instruments:
 
* 6221 Keithley Precision DC and AC+DC Low Noise Current Source
* 2000 Keithley Precision Multimeter
* 5110 EG&G Princeton Applied Research Lock-In Amplifier
* KUSB-3116 Keithley 16-Bit USB DAQ Module

As a result I have written 9 Pre-Alpha versions, 6 Alpha versions and 3 Beta versions.

The current version is [Beta Ver 1.2.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Beta/Beta%20Ver%201.2.vi). 

## Details 

#### **Instruments**

Most of the instruments did not give any trouble while indtalling all the necessary libraries. Practically all of them had a support from National Instruments. However, Lock-In's libs were a little bit outdated, so I had to fix it by replacing the 'Visa open' function with the new one.

To our greatest fears the DAQ was ~~a pain in the ass~~. Not only did it have faulty drivers, it also got possesed by a demon. Actually, Keithley company was purchased by Tektronix and consequently they canceled the support for this product. As a result, the libs could only be installed only on the *LabVIEW 7.1*. After some magic was applied I found the original company who producers the original DAQ boards and got from their official website all the needed drivers and libs.

#### **Software**

Here I will explain the main parts in order for the users to speed up the compilation process.

1. **[Beta Ver 1.2.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Beta/Beta%20Ver%201.2.vi)**

This is the main VI which acquires data from  our instruments writes it into the measurement file and also represents it in the real time plot figure. 

2. **[File creation.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Folder_file_subvi/folder_creation.vi)**

This subVI creates the measurement file in this pattern: *'hh_mm_ss.dat'*. It can be used in other projects.

3. **[Folder creation.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/Folder_file_subvi/file_creation.vi)**

This subVI checks if the folder has already been created or creates one in this pattern: *'prename_dd_mm_yyyy'*.  It can be used in other projects too.

4. **[Instruments Readings.vi](https://github.com/lordonium/Labview-Acquisition-Software/blob/master/instr_comments_readings/com_inst.vi)**

This subVI outputs a string with initial instruments' settings that is futher written into the measurements file. As a part of the experiments the users need to know how the instruments were configured before the start.

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

```
# First test 24/11/17
# Lock-In: 5110 Sensitivity: 100mV Time Constant: MIN | | Keithley: 6221 Start current: -1.00E-6 A Stop current: 1.00E-6 A
# t, ms   6221, A      2000, V      5110_X, V      5110_Y, V    DAQ A0, V      DAQ A1, V    DAQ A2, V    DAQ A3, V     DAQ A4, V     
00000649  -1.00E-6    -0.015887     3.21000E-3    3.2400E-3    1.6174E-2     0.0000E+0   -3.0518E-4     0.0000E+0      0.000305 
00002084  -9.60E-7    -0.015931     3.75000E-3    1.5900E-3    1.7090E-2    -3.0518E-4   -3.0518E-4     0.0000E+0      0.000000 
00003000  -9.20E-7    -0.015444     4.38000E-3    3.2900E-3    1.7090E-2    -6.1035E-4   -3.0518E-4     0.0000E+0     -0.000305 
00004000  -8.80E-7    -0.015236     2.94000E-3    3.2800E-3    1.7090E-2    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00005000  -8.40E-7    -0.014789     3.09000E-3    3.2800E-3    1.6479E-2     0.0000E+0   -3.0518E-4     0.0000E+0     -0.000305 
00006000  -8.00E-7    -0.014910     3.33000E-3    3.1600E-3    1.5869E-2    -6.1035E-4   -3.0518E-4    -3.0518E-4      0.000000 
00007000  -7.60E-7    -0.014421     3.74000E-3    3.0400E-3    1.5869E-2    -9.1553E-4    0.0000E+0    -3.0518E-4     -0.000305 
00008000  -7.20E-7    -0.013843     3.71000E-3    2.6500E-3    1.6174E-2     0.0000E+0    0.0000E+0    -3.0518E-4      0.000305 
00009000  -6.80E-7    -0.013530     3.66000E-3    1.8500E-3    1.5259E-2    -3.0518E-4    0.0000E+0     3.0518E-4     -0.000305 
00010000  -6.40E-7    -0.013469     3.73000E-3    1.4700E-3    1.5259E-2     0.0000E+0    0.0000E+0    -3.0518E-4     -0.000610 
00011000  -6.00E-7    -0.013030     4.41000E-3    1.6300E-3    1.4648E-2    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00012000  -5.60E-7    -0.012609     4.52000E-3    1.6200E-3    1.4343E-2    -3.0518E-4    0.0000E+0     0.0000E+0     -0.000305 
00013000  -5.20E-7    -0.012459     4.51000E-3    1.6900E-3    1.4648E-2    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000305 
00014000  -4.80E-7    -0.011873     4.50000E-3    2.0000E-3    1.3428E-2     0.0000E+0    3.0518E-4    -3.0518E-4     -0.000305 
00015000  -4.40E-7    -0.011823     4.48000E-3    2.7400E-3    1.3733E-2    -3.0518E-4   -3.0518E-4     3.0518E-4     -0.000305 
00016000  -4.00E-7    -0.011627     4.53000E-3    3.2700E-3    1.3123E-2     0.0000E+0   -3.0518E-4     0.0000E+0     -0.000305 
00017000  -3.60E-7    -0.011158     2.90000E-3    3.3200E-3    1.3123E-2     0.0000E+0   -3.0518E-4    -6.1035E-4      0.000000 
00018000  -3.20E-7    -0.010814     4.39000E-3    3.3100E-3    1.2207E-2    -3.0518E-4   -3.0518E-4    -6.1035E-4      0.000305 
00019000  -2.80E-7    -0.010304     4.06000E-3    3.2400E-3    1.3428E-2     0.0000E+0   -3.0518E-4     0.0000E+0     -0.000305 
00020000  -2.40E-7    -0.010340     3.79000E-3    3.2800E-3    1.1597E-2    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000610 
00021000  -2.00E-7    -0.009283     2.93000E-3    5.6000E-4    1.1292E-2     6.1035E-4   -6.1035E-4     0.0000E+0     -0.000305 
00022000  -1.60E-7    -0.009657     2.91000E-3    1.2000E-4    1.1597E-2    -3.0518E-4   -6.1035E-4    -3.0518E-4      0.000305 
00023000  -1.20E-7    -0.003828     4.32000E-3    3.2800E-3    1.0986E-2     0.0000E+0    0.0000E+0    -3.0518E-4     -0.000305 
00024000  -8.00E-8    -0.008989     4.26000E-3    3.2800E-3    1.1536E-1    -3.0518E-4   -3.0518E-4     0.0000E+0      0.000000 
00025000  -4.00E-8    -0.008031     3.84000E-3    3.3500E-3    1.0406E-1     0.0000E+0   -3.0518E-4     0.0000E+0     -0.000610 
00026000   0.00E+0    -0.007406     3.33000E-3    3.2200E-3    9.6741E-2    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000305 
00027000   4.00E-8    -0.007086     3.72000E-3    3.1300E-3    9.1248E-2    -3.0518E-4    6.1035E-4    -3.0518E-4     -0.000610 
00028000   8.00E-8    -0.006397     3.76000E-3    2.9900E-3    8.6670E-2    -3.0518E-4    0.0000E+0    -3.0518E-4     -0.000305 
00029000   1.20E-7    -0.004044     3.77000E-3    2.8200E-3    1.3031E-1    -3.0518E-4    3.0518E-4     3.0518E-4     -0.000610 
00030000   1.60E-7    -0.003406     3.72000E-3    2.0100E-3    5.0842E-1     0.0000E+0   -3.0518E-4    -3.0518E-4      0.000000 
00031000   2.00E-7    -0.003252     3.75000E-3    1.4500E-3    5.2307E-1    -3.0518E-4   -3.0518E-4     0.0000E+0      0.000610 
00032000   2.40E-7    -0.002782     3.74000E-3    1.5000E-3    4.9469E-1    -3.0518E-4   -3.0518E-4     0.0000E+0      0.000305 
00033000   2.80E-7    -0.004317     3.70000E-3    1.6500E-3    4.6997E-1     0.0000E+0   -3.0518E-4     0.0000E+0      0.000000 
00034000   3.20E-7    -0.004317     3.75000E-3    1.6500E-3    1.0437E-1    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000305 
00035000   3.60E-7    -0.004301     3.72000E-3    1.6200E-3    1.2512E-2    -3.0518E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00036000   4.00E-7    -0.003847     3.65000E-3    1.6600E-3    6.1035E-3     0.0000E+0    3.0518E-4     0.0000E+0      0.000000 
00037000   4.40E-7    -0.003496     3.59000E-3    1.7200E-3    4.8828E-3     0.0000E+0    3.0518E-4    -6.1035E-4     -0.000305 
00038000   4.80E-7    -0.003324     3.40000E-3    1.6800E-3    4.5776E-3    -3.0518E-4   -3.0518E-4     3.0518E-4     -0.000916 
00039000   5.20E-7    -0.003129     3.28000E-3    1.6200E-3    3.9673E-3     0.0000E+0    0.0000E+0    -3.0518E-4     -0.000305 
00040000   5.60E-7    -0.002934     2.90000E-3    1.7300E-3    4.5776E-3    -3.0518E-4   -6.1035E-4    -3.0518E-4     -0.000610 
00041000   6.00E-7    -0.002698     2.93000E-3    1.7600E-3    3.9673E-3     0.0000E+0    0.0000E+0     0.0000E+0     -0.000305 
00042000   6.40E-7    -0.000934     2.88000E-3    1.6300E-3    3.9673E-3     0.0000E+0   -3.0518E-4    -3.0518E-4      0.000000 
00043000   6.80E-7    -0.000792     2.97000E-3    1.0300E-3    3.3569E-3    -3.0518E-4    3.0518E-4     0.0000E+0      0.000000 
00044000   7.20E-7    -0.000696     2.99000E-3    6.6000E-4    2.1362E-3     0.0000E+0   -3.0518E-4    -3.0518E-4     -0.000305 
00045000   7.60E-7    -0.000393     2.94000E-3    3.3500E-3    3.3569E-3     0.0000E+0    0.0000E+0    -6.1035E-4     -0.000610 
00046000   8.00E-7     0.000189     2.95000E-3    3.3000E-3    2.7466E-3    -6.1035E-4   -3.0518E-4    -3.0518E-4     -0.000305 
00047000   8.40E-7     0.000145     2.97000E-3   -3.0000E-5    2.7466E-3    -6.1035E-4   -3.0518E-4    -6.1035E-4     -0.000305 
00048000   8.80E-7     0.000238     3.10000E-3   -1.0000E-5    2.7466E-3     0.0000E+0   -3.0518E-4    -6.1035E-4      0.000000 
00049000   9.20E-7    -0.000703     3.07000E-3   -3.0000E-5    2.7466E-3    -3.0518E-4    0.0000E+0    -3.0518E-4      0.000000 
00050000   9.60E-7     0.003388     3.55000E-3    5.0000E-5    1.5259E-3    -3.0518E-4   -3.0518E-4     0.0000E+0     -0.000610 
00051000   1.00E-6     0.003913     3.71000E-3    2.7700E-3    1.8311E-3    -3.0518E-4    0.0000E+0    -3.0518E-4      0.000000 
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

* Arutyгnov Konstantin Yurievich (for an exciting opportunity to work on this amazing project)
* Zavyalov Vitaly Vadimovich (inspiring ideas about DAQ and software in general)
* Khaldeev Stanislav Igorevich (amazing tips about the code) 

