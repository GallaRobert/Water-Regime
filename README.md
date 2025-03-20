# Water Regime Model
# Definition:
The water regime is the prevailing water flow pattern over time. More specifically, it refers to the duration and timing of flooding resulting from surface water (overland flow), or precipitation
# Alternate Wetting and Drying (AWD):
is an irrigation method where water is applied a few days after ponded water disappears.
AWD can be assessed using Traditional methods such as small sample surveys, expert interviews, or household surveys. Nevertheless, it is time-consuming, costly, and subjective.
Currently, Remote Sensing is being used for AWD monitoring; it has more advantages than the traditional method. For instance, Sentinel-1 radar data enables change detection in a time-series Wetness Index (WI)and helps determine AWD adoption across large geographic areas efficiently.
# AWD Model Development:
Figure (1) below illustrates the process of the AWD model, which used Sentinel 1 to calculate the Wetness Index (WI), create WI time series change detection, and develop a classification scheme to average the change index across time.
 
Figure 1 AWD Model schematic 

The sigma0 backscattered coefficient is converted to Beta0 using the equation below. Where:
-	σ0 (Sigma0) is the backscatter intensity,
-	θ (incidence angle) is the angle between the radar beam and the ground
 
Wetness Index (WI) is an index that is used to measure the Soil Water Content and is calculated using the equation:
WI = (VV- min)/ (max-min)
WI negative values represent dryness, and positive values represent wetness 
AWD Model Process:
#1-	Define parameters (startDate and endDate)
#2-	Load sentinel1image collection and filtering using relativeOrbitNumber_start , 32 to get images from one orbit.
#3-	Aggregate to 7-day composites remove empty composites and create a collection image 
#4-	Convert Sigma0 to Beta0 (Beta = Sigma0 / cos(incidence_angle)), apply calibration and median smoothing
#5-	Compute min and max for normalization
#6-	Compute the wetness index (WI)
#7-	Create WI change between consecutive acquisition
#8-	Load and filter the dynamic world collection
#9-	Extract crops and flooded vegetation 
#10-	Create I change between consecutive acquisitions (for crops only)
#11-	Compute the average WI change for crops
#12-	Make a classification based on WI change (only for crops areas)
#13-	Smoothed WI change for crops
#14-	Compute area per pixel in square kilometres  
#15-	Compute the total area per class
#16-	Extract class areas and format data for plotting
#17-	Create a function to format class names and areas 
#18-	 Apply function to each element in class data 
#19-	Get data from the feature collection 
#20-	Define colours for the classes and plot the pie chart  





