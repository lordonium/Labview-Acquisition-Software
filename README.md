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

