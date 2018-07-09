### DIA-NN

DIA-NN - a fast and easy to use tool for processing data independent acquisition (DIA) proteomics data.  
DIA-NN implements deep neural networks to improve precursor ion identification. 
DIA-NN now also supports library-free search and spectral library generation.

**DIA-NN: Deep neural networks substantially improve the   
identification performance of Data-independent acquisition (DIA) in proteomics**  
Vadim Demichev, Christoph B. Messner, Kathryn S. Lilley, Markus Ralser  
https://doi.org/10.1101/282699

DIA-NN encompasses all stages of DIA-MS data processing in a single program.   
As input it takes raw data files and a spectral library.  
A report with protein and precursor ion quantities is produced.  

### Installation

None required. Two executables are provided: DiaNN.exe (a command-line tool) and DIA-NN.exe (a GUI implemented as a wrapper for DiaNN.exe).

### Input files

Raw data files: Thermo .raw, .mzML or .dia (format used by DIA-NN to store spectra).  
The .mzML files should be centroided and contain data as spectra (e.g. SWATH) and not chromatograms.  

Spectral library: comma-separated (.csv) or tab-separated (.tsv or .txt) file.   

### Command-line tool usage
```
diann.exe [commands]  
```
Commands can be supplied in arbitrary order.     

#### Required commands:  
```
--f <data file> 
```
Specifies a data file to be processed. Use --f for each file to be processed. 
```
--lib <spectral library file>
```
Specifies the spectral library. Example:
```
diann.exe --f run1.mzML --f run2.mzML --lib yeast.csv  
```
#### Auxiliary commands:  
```
--cfg <config file> 
```
Specifies a file with a set of commands.
```
--dif <folder> 
```
Specifies a folder containing raw files to be processed.
```
--threads <thread number> 
```
Specifies the number of CPU threads to be used.  
```
--convert
```
With this option DIA-NN converts .mzML files (specified using the --f command) to the .dia format. Unlike .mzML files, .dia files can be loaded quickly (seconds), so it is recommended to convert files that are going to be analysed multiple times.    
```
--ext <string>
```
Add a string to the end of each file name (specified with --f).  
```
--prefix <string>
```
Add a string to the beginning of each file name.  
```
--out <output file> 
```
Specifies the output file; by default, the output is saved to quant.csv in the current working directory.

#### Example:
```
diann.exe --threads 4 --f run1 --f run2 --lib yeast.csv --prefix C:\Data\ --ext .mzML --out run1_2.csv    
```

For a full list of supported commands see the arguments() function in /src/diann.cpp.    

### Building

A Visual C++ solution file is provided with the source code for building on Windows. It should also be possible to buld DIA-NN on Linux, as all the libraries it utilises are compatible with Linux. However, so far it has only been tested on Windows.    





