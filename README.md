# Probabilistic-Relaxation-for-ICESat
This repository provides the source codes of Probabilistic Relaxation method for improving ICESat/GLAS data.

The zipped file contains the source codes and the example data for the algorithm.

The algorithm is implemented as an ESRI ArcMap add-in within the environment of Visual Studio 2017. Therefore, to run this algorithm, ArcGIS Desktop 10.6.1 and Visual Studio 2017 (Community) are required on your computer.

The ArcMap Add-in is a toolbar that contains five buttons. Each button corresponds to one step of algorithm implementation, as described below.

The implementation of the algorithm is divided into five steps. Each step requires one or two inputs and produces one or two outputs.

Step1: Read and smooth (filter)the original ICESat waveform. At this step, the input is a shapefile (e.g. lake.shp or greenland.shp provided in the data folder) and the output is a binary data file (e.g. Step1_ReadAndSmoothWF.dat).

Step2: Align the waveforms in the profile (e.g. lake profile or ice sheet profile) together and extract the signal region of each waveform. The input is the binary data file from Step 1 and the outputs are two binary data files, e.g. Step2_AlignedFullWF.dat and Step2_AlignedSignalWF.dat

Step3: Identify the initial peaks on each waveform and estimate roughly the parameters (e.g. location, amplitude, width) of each peak. The input is the binary file Step2_AlignedSignalWF.dat and the output is Step3_InitialPeakParameters.dat.

Step4: Perform Gaussian fitting on each waveform and refine the parameter estimates for each peak on the waveform. The input is Step3_InitialPeakParameters.dat and the output is Step4_FittedPeakParameters.dat.

Step 5: Perform probabilistic relaxation algorithm to identify the true signal peak on each waveform and calculate the corresponding elevation value for the peak. There are two inputs for this step, Step2_AlignedFullWF.dat and Step4_FittedPeakParameters.dat. The output is an Excel sheet that contains the elevation values produced by the standard retracking algorithm (e.g. Centroid or MAP), the elevation values produced by Probabilistic Relaxation algorithm, and the elevation values obtained from validation DEM (e.g. IceBridge, Arctic DEM and SRTM).
 
