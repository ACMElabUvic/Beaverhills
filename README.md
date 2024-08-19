# Beaverhills Biosphere
This repository contains data, R scripts and associated outputs, and other materials necessary for the Applied Conservation and Macro Ecology (ACME) laboratory's research program in the Beaverhills Biosphere area.
<hr>

### GENERAL INFORMATION

**Project Information**   
The Beaverhills Biosphere is located in east central Alberta, it is a network of protected area spanning approximately 1500 km2. The most recent research in Beaver Hills concluded in 2019 and looked at connectivity within and among protected areas. Camera data was collected in two "sessions" from November 2013 to June 2014, and from December 2015 to April 2016. 

For additional details for the Beaverhills Biosphere research program [here](http://www.acmelab.ca/willmore.html).

Also visit the [ACME website](http://www.acmelab.ca) more information about the ACME lab and other related projects.

**Author Information (data):**  
 Principal Investigator Contact Information  
 Name: Jason T. Fisher, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [fisherj@uvic.ca](mailto:fisherj@uvic.ca) 

 **Author Information (data):**  
 Principal Investigator Contact Information  
 Name: Frances E.C. Stewart, PhD   
 Institution: Wilfrid Laurier University 
 Email: [fstewart@wlu.ca](mailto:fstewart@wlu.ca) 

**Author Information (code):**  
 Data Analysis Contact Information  
 Name: Andrew Barnas, PhD   
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [andrew.f.barnas@gmail.com](mailto:andrew.f.barnas@gmail.com) 

 **Author Information (code):**  
 Data Analysis Contact Information  
 Name: Emerald Arthurs  
 Institution: University of Victoria  
 Address: 3800 Finnerty Rd, Victoria, BC V8P 5C2  
 Email: [emeraldarthurs@uvic.ca](mailto:emeraldarthurs@uvic.ca) 

### DATA & FILE OVERVIEW
**inputs**

This folder contains both summarized and raw data data products (e.g. raw camera trap data csv files) used to produce key products in the outputs folder. 
*Files in main folder*
1) MMP_AllCAMERADATA_2014_2016_v1.csv: this is a summarised file of images taken from each camera site. Data is organized in wide format, such that there are multiple columns detailing whether or not individual species were detected in each image. This has been summarised into long format in the 1. Data Prep.Rmd file. Note that individual timelapse files did exist on the ACME Google drive for this project, but they were difficult to interpret. 
2) SiteData2014.csv: This is a file that contained plenty of information for each camera site, but all that is used from this file is the easting and northing location
3) SiteData2016.csv: Similar to the above file, but as cameras operated in two distinct "sessions" and there was a seperate file for 2016, I felt it necessary to include both files incase gps locations differed between years.
4) Beaverhills_HFI.csv: human features index for each camera site. Re-extracted in August 2024 by Emerald Arthurs. Values represent the proportion of circular buffers around each camera site occupied by each of the individual features. For details see below.
5) Beaverhills_landcover.csv: natural landcover variables for each camera site. Re-extracted in August 2024 by Emerald Arthurs. Values represent the proportion of circular buffers around each camera site occupied by each of the individual features. For details see below. 
   

**outputs**

This folder contains four data products needed to move forward with additional analyses; 1) the raw detections recorded from cameras (blank images have been removed), 2) a summary of independent detections of wildlife species at each camera site to the standard 30 minute threshold, 3) the GPS locations of individual camera sites (details below), and 4) the covariate file for each camera site (details below)

Landcover data for this camera array was re-extracted in August 2024 by Emerald Arthurs. See below. 

**relevant literature**  
This folder provides pdf copies of previously published papers using the Beaverhills Biosphere remote camera dataset. The purpose of this folder is to provide background/information on previously published work using this dataset. Note that sample numbers may vary between individual manuscripts due to specifics of individual projects, as well as the multiple deployment designs within the Willmore dataset.
 * Stewart 2019 - PhD Dissertation UVIC - Understanding and sampling spatial ecological process for biodiversity conservation in heterogeneous lanscapes
 * Stewart et al. 2019. The debate about bait- a red herring in wildlife research
 * Stewart et al. 2019. Protected areas alone rarely predict mammalian biodiversity across spatial scales in an Albertan working landscape
 * Stewart et al. 2018 Species occurrence data reflect the magnitude of animal movements better than the proximity of animal space use
 * Stewart et al. 2017 Distinguising reintroduction from recolonization with genetic testings
 * Burgar et al. 2018 Estimating density for species conservation - comparing camera trap spatial count models to genetic spatial capture-recapture models
 * Barnas et al. 2024 How landscape traits affect boreal mammal responses to anthropogenic disturbance.

**metadata**

This folder contains metadata for the natural landcover and human features index extracted for each camera site. 
* HFI2014_V2_Metadata.pdf: Gives information for all HFI features from 2014 EXCEPT pipelines
* HFI_2010_v2_0_Metadata_v20230809.pdf: Gives information for pipelines which was the only variable not available in the 2014 file
*LandcoverMapABMIGuide2010v1.0.pdf: Gives information on natural landcover features from 2010

<hr>

### **DETAILS ON OUTPUTS** 
### Data specific information for : [outputs/beaverhills_camop.csv]  

* **Number of variables/columns:** 6
* **Number of observations/rows:** 129 (two per camera site) 

**Variable List:**
* **site** : camera site ID
* **session** : as cameras operated from about November 2013 to June 2014, and then December 2015 to April 2016, I added a session identifier
* **start_date** : first day of camera operation as recorded by a camera trigger (no timelapse function used)
* **end_date** : last day of camera operation as recorded by a camera trigger (no timelapse function used)
* **Easting** : camera site Easting location (UTM zone 12N)
* **Northing** : camera site Northing location (UTM zone 12N)


### Data specific information for : [outputs/beaverhills_detections_raw.csv]  

* **Number of variables/columns:** 3
* **Number of observations/rows:** 147875

**Variable List:**
* **site** : camera site ID
* **datetime** : the datetime (year-month-day hour:minute:second) of the first camera image of each independent detection. Multiple images may be taken during a detection event Note there was an error in the raw data resulting in no "seconds" being recorded from the timelapse data, therefore all detections end at the top of the hour (e.g. 6:03:00 AM). This should be of little consequence, but is annoying and results in apparent repeat rows of data for observations within the same minute. 
* **species** : the species in the independent detection. Note this still contains "Other" and some species likely not of interest, so this will need to be filtered/cleaned before any analysis.

### Data specific information for : [outputs/beaverhills_30min_independent_detections.csv]  

* **Number of variables/columns:** 5
* **Number of observations/rows:** 8126 (one row for each independent detection of a species at each site) 

**Variable List:**
* **site** : camera site ID
* **datetime** : the datetime (year-month-day hour:minute:second) of the first camera image of each independent detection. Multiple images may be taken during a detection event Note there was an error in the raw data resulting in no "seconds" being recorded from the timelapse data, therefore all detections end at the top of the hour (e.g. 6:03:00 AM). This should be of little consequence, but is annoying and results in apparent repeat rows of data for observations within the same minute. 
* **species** : the species in the independent detection. Note this still contains "Other" and some species likely not of interest, so this will need to be filtered/cleaned before any analysis.
* **timediff** : the difference in time between subsequent independent detections (mins). Note this could be calculated using the datetime column between subsequent detections. NA's represent the first detection of a species at a given camera, as there can be no difference in time from this event to a previous event. 
* **Event.ID** : a unique identifier for a species' independent detection at a camera site.

### Data specific information for : [outputs/beaverhills_covariates.csv]  

Human Features Index data was extracted from the 2014 Alberta Biodiversity Monitoring Instute Human Footprint Inventory for all variables EXCEPT pipelines. Due to licensing issues or something, data for pipelines was extracted from the 2010 inventory. Both files are located in the metadata folder. Since there are so many variables included here, I am not going to write out all the descriptions but leave the onus to interested users to read the metadata. 

An important note from E.A.: The HFI polygons also seem to overlap a potentially a bit more than I noticed in the other years - example is some cultivation polygons overlap with residential and well sites. Not sure if this is important but just noticed it, this means that the total of all the categories will not necessarily equal to the proportion of a buffer covered by all human feature polygons, but each proportion is relative to the feature within the buffer.

Similarly, natural landcover data was extracted from the ABMI 2010 wall-to-wall inventory, and I leave it to readers to review the metadata provided.

* **Number of variables/columns:** 76
* **Number of observations/rows:** 1280 (one row for each radius at each camera site) 

**Variable List:** (truncated)
* **site** : camera site ID
* **radius**: the circular buffer (meters) around each camera site for which variables were extracted


