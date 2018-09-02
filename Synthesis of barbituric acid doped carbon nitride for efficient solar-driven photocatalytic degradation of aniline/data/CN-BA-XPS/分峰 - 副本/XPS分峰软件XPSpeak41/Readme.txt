XPS Peak Fitting Program for WIN95/98
XPSPEAK Version 4.0

Introduction
	I had spent >1000 hours on XPS peak fitting when I was a 
graduate student.  During that time, I have dreamed of many 
features in the XPS peak fitting software that could help to obtain 
more information from the XPS peaks and reduce my processing 
time.  In 1994, I wrote a program that converts the Kratos XPS 
spectral files to ASCII data.  Once this program was finished, I 
found that the program could be easily converted to a peak fitting 
program.  Then I added the dreamed features into the program, 
e.g., a better way to locate a point at a noise baseline for the Shirley 
background calculations, combine the two peaks of 2p3/2 and 2p1/2, 
fitting different XPS regions at the same time.

	After the first version and Version 2.0, many people have 
emailed me and gave me a lot of suggestions.  I also found 
additional features that I can put into the program.  The major 
change in Version 3.0 is the addition of Newton`s method for 
optimization.  I found that Newton`s method can greatly reduce the 
optimization time for multiple region peak fitting.  For Version 3.1, 
I have removed all the run-time errors that reported to me.  A 
"Shirley + Linear" background was added.  The "copy to clipboard" 
function was added as requested by a user.  Some other minor 
graphical features were added.  In Version 4.0, the asymmetrical 
peak function, three additional file formats for import and a few 
minor adjustments were added.  However, the addition of 
asymmetrical peak function actually requires me to change the 
peak function from the Gaussian-Lorentzian product function 
to the Gaussian-Lorentzian sum function.  Calculation of the 
asymmetrical function using the Gaussian-Lorentzian product 
function is too difficult to implement.  I also realize that the 
software of our newly acquired Phi's Quantum 2000 XPS system 
uses the Gaussian-Lorentzian sum function while the software of 
our Kratos XPS system uses the Gaussian-Lorentzian product 
function.  Therefore, I implemented both functions in the program.  
The user can select the function type in the Options window.  
However, the value of %Gaussian-Lorentzian parameter is 
different in these two functions.  If the selection is the sum 
function, when the user opens a *.xps file that was optimized 
using the Gaussian-Lorentzian production function, you have 
to re-optimize the spectra using the Gaussian-Lorentzian sum 
function with a different %Gaussian-Lorentzian value.
	I realized that the program has weakness in the background 
routines.  It seems to me that I have to read a lot of papers in the 
literature in order to revise them.  I will do that in the next version.  
I have tried but I do not know how to do in Visual Basic 6.0 for 
setting some windows permanently in the front of other windows 
and to create a help file.

	This version of the program was written in Visual Basic 6.0 
and uses 32 bit processes.  This is a freeware.  You may ask for the 
source program if you really want to.  I hope this program will be 
useful for people without a modern XPS software.  I also hope that 
the new features in this program can be adopted by the XPS 
manufacturers in the later versions of their software.  If you have 
any questions/suggestions, please send an email to me.
	Raymund W.M. Kwok
	Department of Chemistry
	The Chinese University of Hong Kong
	Shatin, Hong Kong
	Tel: (852)-2609-6261
	Fax:(852)-2603-5057
	email: rmkwok@cuhk.edu.hk

	Finally, I would like to thank the comments and suggestions 
from many people.  For the completion of Version 4.0, I would like 
to think Dr. Bernard J. Flinn for the routine of reading Leybold 
ascii format, Prof. Igor Bello for exporting his spectra into 
VAMAS files from a VG system for the program testing, and my 
graduate students for testing the program.  I hope I will add other 
features into the program in the near future.

Program Installation
	Unzip the XPSPEA4.ZIP file and run Setup.exe program in 
Win 95 or Win 98.

Features of the program
(1)	Peak parameters
	This program uses the following asymmetric Gaussian-
Lorentzian sum function

[Sorry!  Please read readme.doc for the equation]

where  

m=0 for 100% Gaussian
m=1 for 100% Lorentzian
TS and TL are the parameters for the asymmetric tail
TS=0 for symmetric Gaussian-Lorentzian function

and the following symmetrical Gaussian-Lorentzian product 
function

[Sorry!  Please read readme.doc for the equation] 

where  

m=0 for 100% Gaussian
m=1 for 100% Lorentzian

	You can choose the function type in the Options window.  
Select "GL sum" for the Gaussian-Lorentzian sum function and 
"GL product" for the Gaussian-Lorentzian product function.  For 
the Gaussian-Lorentzian sum function, each peak can have six 
parameters, i.e., peak position, area, FWHM, %Gaussian-
Lorentzian, TS and TL.  Each peak in the Gaussian-Lorentzian 
product function can have four parameters, i.e., peak position, area, 
FWHM, and %Gaussian-Lorentzian.  Since peak area relates the 
atomic concentration directly, we use it as a peak parameter and the 
peak height will not be shown to the user.

	For asymmetric peak, the FWHM only refers to the half of 
the peak that is symmetrical.  The actual FWHM of the peak is 
calculated numerically and is shown after the "actual FWHM" in the 
Peak Parameter Window.  If the asymmetric peak is a doublet (p, d 
or f type peak), the "actual FWHM" is the FWHM of the doublet.

(2)	Peak types: p, d and f.
	Each of these peaks combines the two splitting peaks.  The 
FWHM is the same for both the splitting peaks, e.g. a p-type peak 
with FWHM=0.7eV is the combination of a p3/2 with FWHM at 
0.7eV and a p1/2 with FWHM at 0.7eV, and with an area ratio of 2 
to 1.  If the theoretical area ratio is not true for the splitted peaks, 
the old way of setting two s-type peaks and adding the constraints 
should be used.  The “s.o.s.” stands for spin orbital splitting.
Note:	the FWHM of the p, d or f peaks are the FWHM of the p3/2, 
d5/2 or f7/2, respectively.  The FWHM of the combined peaks (e.g. 
combination of p3/2 and p1/2) is shown in the "actual FWHM" in the 
Peak Parameter Window.

(3)	Peak constraints
	Each parameter can be referenced to the same type of 
parameters in other peaks.  For example, for four peaks (Peak#0, 1, 
2 and 3) with known relative peak positions (0.5eV between 
adjacent peaks) , the following can be used
	Position: Peak 1 = Peak 0 + 0.5eV
	Position: Peak 2 = Peak 1 + 0.5eV
	Position: Peak 3 = Peak 2 + 0.5eV
You may reference to any peaks except with looped references.
	The optimisation of the %GL value is allowed in this 
program.  A suggestion to use this feature is to find a nice peak for 
a certain setting of your instrument and optimise the %GL for this 
peak.  Then fix the %GL in the later peak fitting process when the 
same instrument settings were used.
	This version also includes the setting of the upper and lower 
bounds for each parameter.

(4)	Background
	This program provides the choices of Shirley, Linear or 
Tougaard backgrounds.  For Tougaard background, the program 
can optimize the B1 parameter by minimizing the "square of the 
difference" of the intensities of ten data points in the high binding 
energy side of the range with the intensities of the calculated 
background.
	Averaging at the end points of the background can reduce 
the time to find a point at the middle of a noisy baseline.  The 
program includes the choices of None (1 point), 3, 5, 7, and 9 point 
average.  This will average the intensities around the binding energy 
you selected.
	The "Shirley + Linear" background was added for sloped 
background.  The "Shirley + Linear" background is the Shirley 
background plus a straight line with starting point at the low BE 
end-point and with a slope value.  If the slope value is zero, the 
original Shirley calculation is used.  If the slope value is positive, 
the straight line has higher values at the high BE side, which can be 
used for spectra with higher background intensities at the high BE 
side.  Similarly, a negative slope value can be used for a spectrum 
with lower background intensities at the high BE side.  The 
optimization button may be used when the Shirley background is 
higher than the signal intensities.  The program will increase the 
slope value until the Shirley background is below the signal 
intensities.  Please see the example: Cu2p_bg.xps.
	I believe that the background subtraction calculation cannot 
remove exactly the background signals.  For quantitative studies, 
the best procedure is "consistency".  

(5)	Optimization
	You can optimize a single peak parameter, the peak (the 
peak position, area, FWHM, and the %GL if the "fix" box is not 
ticked), a single region (all the parameters of all the peaks in that 
region if the "fix" box is not ticked), or all the regions.  During 
optimization, you can press the "Cancel" button and the program 
will stop the process in the next cycle.

(6)	Options of the program
	The %tolerence allows the optimization routine to stop if 
the change in the "difference" after one loop is less that the 
%tolerence.  The default setting of the optimization is Newton's 
method.  This method requires a delta value for the optimization 
calculations.  You may need to change the value in some cases, but 
I found that the existing setting is enough for all of my data.
	For the binary search method, it searches the best fit for 
each parameter in up to four levels of value ranges.  For example, 
for a peak position, in first level, it calculates the chi^2 when the 
peak position is changed by +2eV, +1.5eV, +1eV, +0.5eV, -0.5eV, 
-1eV, -1.5eV, and -2eV (range 2eV, step 0.5eV).  Then, it selects 
the position value that gives the lowest chi^2.  In the second level, 
it search the best values in the range +0.4eV, +0.3eV, +0.2eV, 
+0.1eV, -0.1eV, -0.2eV, -0.3eV, and -0.4eV (range 0.4eV, step 
0.1eV).  In the third level, it selects the best value in +0.09eV, 
+0.08eV, ...+0.01eV, -0.01eV, ...-0.09eV.  This will give the best 
value with two digits after decimal.  Level 4 is not used in the 
default setting.  The range setting and the number of levels in the 
option window can be changed if needed.
	The Newton's Method or Binary Search Method can be 
selected by clicking the "use" selection box of that method.
	The selection of the peak function is also in the Options 
window.
	The user can save/read the option parameters with the file 
extension *.opa.  The program reads default.opa file at the 
beginning of its running.  Therefore, the user can customize the 
program options by saving the selections into the default.opa file.

(7)	Region Shift
	A "Region Shift" parameter was added under the 
"Parameters" menu.  I intend to use this parameter to compensate 
the charging effect, fermi level shift or change in system work 
function.  This value will be added to all the peak positions in the 
region for fitting purposes.
	An example:
	A polymer surface is positively charged and all the peaks are 
shifted to the high binding energy by +0.5eV, e.g. aliphatic carbon 
at 285.0eV shifts to 285.5eV.  When the Region Shift parameter is 
set to +0.5eV, 0.5eV will be added to all the peak positions in the 
region during peak fitting.  But the listed peak positions are not 
changed, e.g. 285.0eV for aliphatic carbon. 

(8)	Import
	The program can read the Kratos's *.DES files together 
with the peak fitting parameters in the file, the ASCII files exported 
from Phi's Multiplex software, the ASCII files of Leybold's 
software and the VAMAS file format.  For the Phi and Leybold, 
multiple regions can be read.  For the VAMAS import, I have 
tested only the 1988 format exported by the VG ESCALAB-220’s 
software.  I guess the program should be able to read the later 
version of the format, but only limited to the first region.  If 
someone can provide me a multiple region VAMAS file, I can add 
this in.  The program can also import ASCII file in the following 
format:

	Binding Energy Value 1 	Intensity Value 1
	Binding Energy Value 2 	Intensity Value 2
 		    ..			  	..

The B.E. list must be in ascending or descending order, and the 
separation of adjacent B.E.s must be the same .  However, the file 
cannot have other lines before and after the data, and sometimes, 
TAB may cause reading error.

(9)	Export
	The program can export the ASCII file of spectrum 
(*.DAT) for making high quality figures using other software (e.g. 
SigmaPlot).  It can export the parameters (*.PAR) for further 
calculations (e.g. use Excel for atomic ratio calculations).  It can 
also copy the spectral image to the system clipboard so that the 
spectral image can be pasted into a document (e.g. MS WORD).

(10)	File I/O
	The program can store all the peak information into a 
*.XPS file for later use.  The file format of XPSPEAK 4.0 is 
different from XPSPEAK 3.1, 3.0 and 2.0.  However, XPSPEAK 
4.0 can read the file format of XPSPEAK 3.1, 3.0 and 2.0, but not 
the reverse.
	The program can also store/read the peak parameter files 
*.RPA so that you do not need to re-type all the parameters again 
for a similar spectrum. 

Limitations
	This program limits the maximum number of points for each 
spectrum to 5000 and the maximum of peaks for all the regions to 
51.  For each region, the maximum number of peaks are 10.

Warning for peak fitting
	I found that some graduate students believe that the fitting 
parameters for the best fitted spectrum is the "final answer".  This is 
definitely not true.  Adding enough peaks can always fit a spectrum.  
Peak fitting only assists the verification of a model.  The user must 
have a model in mind before adding peaks to the spectrum!  

Sample Files:
(i)	gaas.xps:  a file contains 10 spectra
	Use Open to retrieve the file.  It includes ten regions, 1-4 
for Ga 3d, 5-8 for Ga 3d and 9-10 for S 2p.  For the Ga 3d 
and As 3d, the peaks are d-type with s.o.s.=0.3 and 0.9 
respectively.  Regions 4 and 8 are the sample just after S-
treatment.  Other regions are after annealing.  Peak width of 
Ga 3d and As 3d are constrained to those in regions 1 and 
5.  The fermi level shift of each region was determined using 
the As 3d5/2 peak and the value was put into the "Region 
Shift" of each region.  Since the region shift takes into 
account the Fermi level shift, the peak positions can be 
easily referenced for the same chemical components in 
different regions, i.e. Peak#1, 3, 5 of Ga 3d are set equal to 
Peak#0, and Peak#8, 9, 10 of As 3d are set equal to 
Peak#7.  Note that the %GL value of the peaks is 27% 
using the GL sum function in Version 4.0, while it is 
80% using the GL product function in previous 
versions.

(ii)	Cu2p_bg.xps: background subtraction using Shirley method
	The spectrum was sent to me by Dr. Roland Schlesinger.
	Region 1 shows the problematic background when the 
Shirley background is higher than the signal intensities.  In 
the Shirley calculation routine, some negative values are 
generated and resulted in a non-monotonic increase 
background.
	Region 2 shows a "Shirley + Linear" background.  The 
slope value was input by trial-and-error until the 
background is lower than the signal intensities.
	Region 3 was obtained using the optimization routine.

(iii)	Kratos.des: a Kratos DES file
Use import Kratos to retrieve the file.  Note that the four 
peaks are all s-type.  You may delete peak 2, 4 and change 
the peak 1,3 to d-type with s.o.s. =0.7.  You may also read 
in the parameter file: as3d.rpa.

(iv)	ASCII.prn: an ASCII file
Use import ASCII to retrieve the file.  It is a As 3d 
spectrum of GaAs.  In order to fit the spectrum, you need to 
first add the background and then add two d-type peaks 
with s.o.s.=0.7.  You may also read in the parameter file: 
as3d.rpa.

(v)	Phi.asc: an ASCII file exported from Phi's Multiplex v6.0
	Use import Phi to retrieve the file.  It is a Ag 3d5/2 spectrum.  
You may try to use the following parameters to fit the Ag 
3d5/2 peak: Shirley background, s-type peak, %GL=50, 
TS=0.1 and TL=70.

(vi)	Leybold.asc:  an ASCII file of Leybold format provided by 
Bernard J. Flinn.  It contains four regions.

(vii)	VAMAS.txt: a VAMAS file exported from the VG 
ESCALAB-220's software.


Have Fun!		Dec. 31, 1998.
