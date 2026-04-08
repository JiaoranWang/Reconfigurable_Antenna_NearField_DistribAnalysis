# Near-field Coupling and Current Distribution Evaluation on Reconfigurable Antenna

 the electrical field (E-field) distributions of Tx–Rx antenna system with a homogeneous phantom and the
surface current distribution (J-surf) of the Rx antenna
Are evaluated.




## Electrical Field Analysis Model
## Current Distribution Analysis Model





This readme file contains how to 

The format of .aedtplt is list in 
ANSYS HFSS Exporting Field Plots, and data processing


From <https://ansyshelp.ansys.com/public/Views/Secured/Electronics/v242/en/Subsystems/HFSS/Content/ReportsandPostProc/ExportingFieldPlots.htm> 


Please refer to :
e_field_aedtplt_reconfiguration.py


**• Input:**

<img width="1853" height="978" alt="image" src="https://github.com/user-attachments/assets/726addc3-62ea-4cc1-b2ce-3261dbe7741b" />

<img width="752" height="462" alt="image" src="https://github.com/user-attachments/assets/2d301183-ee56-4664-bb11-c93f6148c465" />



For quantitative near-field comparison, the scalar E-field contour data exported from HFSS were processed in Python. 
For each mode and cut-plane, an ROI centered at the Rx location was defined, and the corresponding E_peak, E_mean, and E_std  values were extracted. These metrics were used to compare the field concentration and uniformity of the different modes.


The Code structure and algorithms in behind is shown in 

<img width="539" height="558" alt="image" src="https://github.com/user-attachments/assets/35075950-69de-4fc7-8625-dfaa866db8d4" />





The input and output accordingly:

Input: 


• Output:

Mode	Plane	ROI_Points	E_peak (V/m)  	E_mean (V/m)	E_standardDeviation (V/m)
[000]	XZ	171	29.046481	21.262479	2.529924
[001]	XZ	142	31.562013	22.399322	3.027829
[010]	XZ	128	30.99616	25.151627	2.66328

……

The overall process is defined as this way:



# Antenna Near-field 

<img width="564" height="963" alt="image" src="https://github.com/user-attachments/assets/c3cae8c4-7ee6-4b33-8b28-091978735a98" />


