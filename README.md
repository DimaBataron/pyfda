pyFDA
======
## Python Filter Design Analysis Tool

The goal of this project is to create a GUI based tool to analyse and design discrete time filters implemented in Python and Qt. 

![Screenshot](images/pyFDA_screenshot.PNG)

Why yet another filter design tool?
* **Education:** There is a very limited choice of user-friendly, license-free tools available to teach the relationship between different filter design methods and specifications and their influence on time and frequency behaviour.
* **Show-off:** Demonstrate that Python is a potent tool for digital signal processing applications as well. The interfaces for textual filter design routines are a nightmare: linear vs. logarithmic specs, frequencies normalized w.r.t. to sampling or Nyquist frequency, -3 dB vs. -6 dB vs. band-edge frequencies ... (This is due to the different backgrounds and the history of filter design algorithms and not Python-specific.)
* **Fixpoint filter design:** Recursive filters have become a niche for experts. Convenient design and simulation support (round-off noise, stability under different quantization options and topologies) could attract more designers to these filters that are easier on hardware resources and much more suitable e.g. for uCs.
* **FPGA design**: Especially on low-budget FPGAs, multipliers are rare. However, there are no good tools for designing and analyzing filters without or with a limited number of multipliers like CIC or LDI-based designs.
* **Filter designs in VHDL**


The following features are currently implemented:

* Easy to use, clearly structured GUI
 * Only widgets needed for the currently selected design method are visible
 * 
* Access Scipy filter design methods with a common interface
 * Currently implemented: Equiripple, Firwin, Chebychev 1 and Chebychev 2 
 * use absolute frequencies or frequencies normalized to sampling or Nyquist frequency
 * specify ripple and attenuations in dB, as voltage or as power ratios
* Easy switching between manual and minimum filter order without losing all the other settings
 * Filter order and corner frequencies calculated by minimum order algorithms can be fine-tuned by hand
* Modular structure, facilitating the implementation of new filter design and analysis methods
 * Filter design files can be added and edited *without* changing or even restarting the program
 * Special widgets needed by the design method (e.g. for choosing the window in Firwin) are included in the filter design file, not in the main program
* Comfortable saving and loading of filter designs as
  * Comma-separated values (CSV)
  * Matlab (R) workspace format

Missing for the first release are the following features (help is very welcome!):
* Testing pyFDA under Python 3.x - so far, the application has been only developed unter Python 2.7 with 3.x in mind (from __future__ ...)
* Filter design methods (some clean-up of the design method files' structure needed before implementing more methods)
 * Butterworth
 * Elliptic
* Graphical analyses (some updates to the plotting infrastructure needed)
 * Pole/Zero plot
 * Impulse response
 * Group delay
* Input widget: displaying and editing filter coefficients and poles / zeros (already started)
* Save and load filter designs (pickle? shelve?)

Plans for following releases are:
* Better help files and messages
* Show error messages and warnings in the GUI
* Design, analysis and export of filters as second-order sections
* Quantization of filter coefficients
* Multiplier-free filter designs (CIC, GCIC, SigmaDelta-Filters, ...)
* Export of Python filter objects
* Analysis of different fixpoint filter topologies (direct form, cascaded form, parallel form, ...) concerning overflow and quantization noise
* Fixpoint filter sythesis and export using the myHDL module (<myhdl.org>)

Further ideas are
* Wave-Digital Filters
* ...

