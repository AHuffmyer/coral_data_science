# Coral Physiology Dataset Information 

This data repository contains data files for coral physiology.  

## Project overview

This data is generated from the [E5 RoL Coral project timeseries respository](https://github.com/urol-e5/timeseries). 

Seasonal cycles in marine ecosystems generate fluctuations in important environmental factors key to triggering or driving life history states (i.e., gametogenesis, spawning, flowering, migration, etc.). Importantly, the seasonally driven change in environmental conditions influences the energetic and, therefore, physiological state of an organism, which is critical to its capacity to respond to environmental stress and perturbations. For reef-building corals, the nutritional symbiosis of the cnidarian host with intracellular single celled dinoflagellates in the Family Symbiodiniaceae, results in a combined responsiveness to fluctuations in temperature, light, and nutrients, all of which change seasonally in tropical oceans. Deviations in these three factors outside of normal ranges are major drivers of dysbiosis of the coral-Symbiodiniaceae relationship that can result in coral bleaching and mass mortality. However, many studies of the effects of these variables take place in the absence of a consideration of the current physiological state of the coral holobiont due to seasonal timing. Here, we used the well-described site of Moorea, French Polynesia to test the effect of seasonal variation from environmentally distinct sites on three dominant and ecologically important genera, *Acropora*, *Pocillopora*, and *Porites*. 

![Sites](https://github.com/urol-e5/timeseries/blob/master/metadata/E5_Sites.png?raw=true)  

We collected samples from coral colonies in January, March, September, and November of 2020 and quantified a suite of physiological variables (13 characteristics measured) in the coral host and algal symbiont, as well as molecular identification of the Symbiodiniaceae community and host species. 

<img width="554" alt="responses" src="https://github.com/urol-e5/timeseries/assets/32178010/733de652-9b2d-49c0-974d-30778f81fbb6">  

Samples were collected from "colonies". Each colony is a biological replicate in this study. Fragments, or small samples, of each colony were collected at each of the time points described above with multiple responses measured on each fragment (e.g. physiological measurements and DNA sequencing). 

15 colonies were tracked and sampled from each species at each site. Metadata for each sample is explained in the dataset descriptions below.  

## Goals 

The goal of this data science collaboration is to conduct analysis of these multivariate datasets to answer the following general questions:  

- What are the primary drivers of seasonal physiological changes in corals? 
- How do these responses differ between species? 
- How are physiological responses influenced by the composition of symbiont communities? 

Two data sets are included in this respository, described below. 

## Dataset 1: Physiology time series

`data/coral_physiology/timeseries_physiology.csv` 

This data set contains time series physiological data from each coral colony at each site. Note that some of the colonies were lost, died, or were not sampled for some metrics. Therefore, this data set contains NAs to represent missing observations. We can retun only complete cases with `complete.cases()` if required.    

Each row corresponds to a colony sampled at a particular timepoint. Columns include the following metadata and responses: 

- `colony_id`: colony ID written as "genus" - "ID number". POC indicates Pocillopora, ACR indicates Acropora, and POR indicates Porites.   
- `host_genus`: Genus of the host coral. Either Acropora, Pocillopora, or Porites. 	
- `timepoint`	: Time point sample was taken. Timepoint 1 = January 2020, Timepoint 2 = March 2020, Timepoint 3 = September 2020, Timepoint 4 = November 2020.  
- `site`: Site of coral colony. Sites are Mahana, Hilton, and Manava (see map above). 	
- `host.afdw.mg.cm2`: Host biomass expressed as mg ash free dry weight (afdw) per cm2 surface area. 	
- `sym.afdw.mg.cm2`: Symbiont biomass expressed as mg ash free dry weight (afdw) per cm2 surface area. 	
- `am`: Maximal photosynthetic rate expressed as µmol oxygen produced per cm2 per hour.  	
- `aqy`: Photosynthetic efficiency (alpha) expressed as apparent quantum yield.  	
- `rd`: Respiration (dark respiration) of the coral host expressed as µmol oxygen per cm2 per hour. 	
- `ik`: Saturating irradiance for photosynthesis, expressed as photosynthetically active radiation (PAR).  	
- `ic`: Compensation irradiance for photosynthesis, expressed as photosynthetically active radiation (PAR).  	
- `calc.umol.cm2.hr`: Calcification rate of the coral, expressed as µmol CaCO3 per cm2 per hour.  
- `cells.mg.afdw`: Number of symbiont cells per mg host biomass (afdw).  	
- `chla.ug.mg.afdw`: Concentration of chlorophyll a pigments, expressed as µg chlorophyll a per mg host biomass (afdw).  	
- `chlc2.ug.mg.afdw`: Concentration of chlorophyll c2 pigments, expressed as µg chlorophyll c2 per mg host biomass (afdw).	
- `prot.mg.mg.afdw`: Total soluble protein, expressed as mg protein per mg host biomass (afdw).	
- `cre.umol.mg.afdw`: Total antioxidant capacity, expressed as µmol copper-reducing elements (CRE) per mg host biomass (afdw).	
- `chla.ug.cell`: Concentration of chlorophyll a pigments, expressed as µg chlorophyll a per symbiont cell.	
- `chlc2.ug.cell`: Concentration of chlorophyll c2 pigments, expressed as µg chlorophyll c2 per symbiont cell.		
- `ratio.afdw.mg.cm2`: Ratio of host to symbiont biomass (mg afdw) per cm2 surface area. 	
- `total.chl.afdw`: Total chlorophyll (a+c2 pigments), expressed as µg chlorophyll  per mg host biomass (afdw).	
- `total.chl.cell`: Total chlorophyll (a+c2 pigments), expressed as µg chlorophyll  per symbiont cell.

## Dataset 2: Symbiont community composition time series 

`data/coral_physiology/symbiont_rel_abund.csv` 

This data set contains time series symbiont community composition data from each coral colony at each site. Community composition data expressed as relative abundance of each detected symbiont strain through DNA amplicon sequencing. 

Note that some of the colonies were lost, died, or were not sampled for some metrics. Therefore, this data set may have fewer observations than the coral physiology data set described above. All colonies in the coral physiology data set are represented here, but there are some colonies for which a timepoint of symbiont community data may be missing, resulting in fewer total observations. 

Each row corresponds to a colony sampled at a particular timepoint. Columns include the following metadata and responses: 

- `colony_id`: colony ID written as "genus" - "ID number". POC indicates Pocillopora, ACR indicates Acropora, and POR indicates Porites.   
- `host_genus`: Genus of the host coral. Either Acropora, Pocillopora, or Porites. 	
- `timepoint`	: Time point sample was taken. Timepoint 1 = January 2020, Timepoint 2 = March 2020, Timepoint 3 = September 2020, Timepoint 4 = November 2020.  
- `site`: Site of coral colony. Sites are Mahana, Hilton, and Manava (see map above). 	

All remaining columns represent an identified symbiont strain. These strains are denoted by the genus letter and numberical values to represent particular strains within the genus. Each column represents a unique strain detected. 

Values in matrix are relative abundance, ranging form 0-1.  

## Contact 

If you have any questions, contact Ariana Huffmyer at ashuffmyer (at) uri.edu. 
