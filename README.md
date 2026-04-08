# Reconfigurable_Antenna_NearField_DistribAnalysis



The format of .aedtplt is list in 
ANSYS HFSS Exporting Field Plots, and data processing


From <https://ansyshelp.ansys.com/public/Views/Secured/Electronics/v242/en/Subsystems/HFSS/Content/ReportsandPostProc/ExportingFieldPlots.htm> 


Please refer to :
e_field_aedtplt_reconfiguration.py


**• Input:**

<img width="1853" height="978" alt="image" src="https://github.com/user-attachments/assets/726addc3-62ea-4cc1-b2ce-3261dbe7741b" />

<img width="752" height="462" alt="image" src="https://github.com/user-attachments/assets/2d301183-ee56-4664-bb11-c93f6148c465" />



	For quantitative near-field comparison, the scalar E-field contour data exported from HFSS were processed in Python. For each mode and cut-plane, an ROI centered at the Rx location was defined, and the corresponding E_peak, E_mean, and E_std  values were extracted. These metrics were used to compare the field concentration and uniformity of the different modes.



The input and output accordingly:

Input: 


• Output:

Mode	Plane	ROI_Points	E_peak (V/m)  	E_mean (V/m)	E_standardDeviation (V/m)
[000]	XZ	171	29.046481	21.262479	2.529924
[001]	XZ	142	31.562013	22.399322	3.027829
[010]	XZ	128	30.99616	25.151627	2.66328

……

The overall process is defined as this way:



<img width="1930" height="3618" alt="image" src="https://github.com/user-attachments/assets/a18ad0d5-3c20-46ac-a05e-35f80fa1f091" />
