# Phylogenetic Biology - Final Project

# An Investigation into the Relationship between Procolophonid Biogeography and Tooth Morphology

# Introduction and Goals

The goal of my project is to answer the following question: are procolophonids that have similar tooth sizes more closely related to one another than procolophonids with differing tooth sizes? I am interested to see if more closely related procolophonids may have more similar diets and lifestyles.

For this project, I will compare the various dentitions of procolophonids, an extinct clade of anapsid reptiles that lived during the late Permian through the Triassic (~300-200 million years ago). Procolophonids are the only clade within the larger clade Parareptilia to survive the Permo-Triassic mass extinction, the most devastating mass extinction to occur in earth’s history (Essentials of Geology). Procolophonids are a large and successful group of parareptiles with more than 30 known genera (Cisneros, 2008). They occupied a wide geographic range, including the Americas, Europe, Asia, Africa, and Antarctica (Dias-de-Silva, Modesto and Schultz, 2006; Cisneros and Ruta, 2010). Research has shown that procolophonids likely had a fossorial (burrowing) lifestyle, feeding on insects and plants (Botha-Brink and Smith, 2012). Most researchers think procolophonids are herbivorous or durophagous, but there no full analysis of procolophonid teeth has been done in relation to their places on the tree of life. 

The methods I will use to do this include phylogenetic generalized least squares (PGLS). The tree I will be using is taken from Cisneros' 2008 paper on procolophonid phylogeny, and I will be using Character #28, which is the presence/absence of labiolingual tooth broadening. Once this analysis is complete, I will then study whether dentition changes correlate with changes in diet. Using procolophonid biogeographical data, which is available in the literature, I will be able to see if shifts in habitat and dentition occur simultaneously. If they do occur simultaneously, it may be hypothesized that a change in diet occurred during this period. 

I will use the R package 'caper' to run the PGLS analysis and do a phylogenetic regression of dentition characters on geography. Instead of using BioGeoBEARS for this analysis of dentition and geographic location, I decided (with the help of Professor Dunn!) to do a regression of dentition characters onto geography. Instead of creating a separate BioGeoBEARS geography text file, I will code the geographical location as a character (using 0 - 6) and add it to the original Nexus file I obtained from Cisneros 2008.

The data I will use is from a character state matrix taken from Cisneros 2008, as well as the phylogeny used. To conduct the initial phylogenetic inference, I will be using traits detailed in Juan C. Cisneros' 2008 paper on procolophonid phylogeny and using this tree (and the traits) to perform a phylogenetic signal analysis based on dentition. Additionally, I will perform a PGLS analysis based on geographic location. This analysis will aid in understanding the evolutionary relationship between dentition and habitat, and it will, hopefully, shed light on procolophonid radiation in the Triassic and diversity in niche occupation. 

Because I suspect that there was a Triassic radiation of procolophonids, I would expect there to be lower association between procolophonids that exhibit vastly different tooth sizes and greater association between procolophonids that have similar tooth sizes (and therefore likely had similar diets and occupied similar niches). 

# Methods

## DATA MATRIX from Cisneros 2008. 

![Cisneros_2008_Data_Matrix](https://github.com/SelenaMart28/finalproject/blob/master/Cisneros2008DataMatrix.JPG?raw=true)

This data matrix was converted into a text file using an OCR, and then this character information was put into Nexus format. This data (in Nexus format) is included in the files of this repository. The tree shown belown was rendered in IcyTree for visualization of the procolophonid phylogeny from Cisneros 2008. This is the original tree, formed from a .nex file that used the data matrix given in Cisneros 2008 (this data matrix was included in-text, but was not included as a separate file in any supplementals, to this student's chagrin). However, eventually, in correspondence with Cisneros, I was able to obtain the proper data/file formats needed for this analysis, which I have included in the repository. 

## Taxa 
Owenettidae   

*Coletta seca*

*Pintosaurus magnidentis*

*Sauropareion anoplus*

*Phaanthosaurus spp.* 

*Eumetabolodon dongshengensis* 

*Theledectes perforatus*

*Tichvinskia vjatkensis*

*Timanophon raridentatus*  

*Kapes spp.*

*Thelephon contritus*

*Eumetabolodon bathycephalus* 

*Procolophon trigoniceps* 

*Thelerpeton oppressus* 

*Teratophon spinigenis* 

*Pentaedrusaurus ordocianus* 

*Neoprocolophon asiaticus*

*Sclerosaurus armatus*

*Scoloparia glyphanodon*

*Leptopleuron lacertinum*

*Soturnia caliodon*

*Hypsognathus fenneri*

*Phonodus dutoitorum*

*Kitchingnathus untabeni*

*Lasasaurus beltanae*

*Anomoiodon liliensterni*

*Procolina teresae*

*Mandaphon nadra*

*Eomurruna yurrgensis*

![Cisneros_2008_Procolophonid_Data_Matrix_Icytree](https://github.com/SelenaMart28/finalproject/blob/master/Cisneros2008ProcolophonidDataMatrixIcyTree.jpeg)

Once this character information was in Nexus format, I then input the file in IQTree using the Grace cluster provided by Yale University. After this tree was rendered by IQTree, I then created a second .nex file that included my data (in the data matrix). Because I did not have tooth width and length data for all of the specimens included in this tree, I put ? to label data as missing, as is standard in the Nexus format. After this was completed, I input this .nex file into IQTree. I was able to fix the errors I kept getting and was able to render a tree in IQTree. 

Following this, I then began to use the 'caper' package (and the PGLS analysis) in R. 

## Geographic Regions 
I first had to compile a list of my geographic regions of interest and their relevance to my taxa of interest. Instead of using political boundaries, I instead use modern continents for this geographic list. Because procolophonids are of Permian and Triassic age, the geographic regions are (quite) different from how they are in the modern day. I am using modern continents for my analysis with caper/PGLS and will then discuss how this geographic distribution would have looked during the Permian and Triassic in the discussion. 

Regions and the number they will be encoded as characters in my Nexus file:

Africa: 0 

South America: 1

North America: 2

Asia: 3

Antarctica: 4

Europe: 5

Oceania: 6

I am planning on adding geographic region as a character to the current Nexus file taken from Cisneros 2008. The list of areas that will be used in this analysis is shown above. The maximum number of areas in the analysis is 7 (1 per state). Because each of the taxa *has* to exist on a continent, the null range will not be included in possible states. I will use the define_tipranges_object to input my geographic data for my taxa of interest. 

## Teeth Morphology (Whether or not teeth are labio-lingually broadened)
Rather than import my own data from my own research (due to time constraints and how I've drawn out this project), I decided in the end to use dentition data taken from the data matrix provided to me by Cisneros. I had my pick of dentition characters and I decided to use "labio-lingual broadening (widening)" as the factor of interest in this project. "Labio" means "towards the front of the mouth", and "lingual" means "towards the back of the mouth". Tooth morpology can be connected to diet, and identifying/understanding the dental morphologies of various animals can aid in determing their potential diets. This is, of course, helpful when working with long-extinct animals, as it can be quite difficult to ascertain their ways of life any other way. 

![Labiolingually-broadened Teeth](https://github.com/SelenaMart28/finalproject/blob/master/FinalProjectLabioLingualTeethImage.JPG)

# Results

## Diagnostic Plots (I)
The first two show the fit of the residuals to a normal distribution: a density plot of the distribution of the residuals and a normal Q-Q plot: the distribution of the residuals against their expected distribution under a normal distribution. These plots are both roughly normal and point towards the normality of our data, giving our analysis viability. 

![Density_Default_Curve](https://github.com/SelenaMart28/finalproject/blob/master/densitydefaultFinalProjectImage.JPG)
![Normal_QQPlot](https://github.com/SelenaMart28/finalproject/blob/master/NormalQQPlotFinalProjectImage.JPG)

## Diagnostic Plots (II)
The second two show the fitted values against both the residuals and the observed value to look for pattern in the residuals within the model. There is a non-random pattern in this model. 

![ResidualValue vs. Fitted Value](https://github.com/SelenaMart28/finalproject/blob/master/ResidualValuevsFittedValueFinalProjectImage.JPG)
![FittedValue vs. Observed Value](https://github.com/SelenaMart28/finalproject/blob/master/FittedValuevsObservedValueFinalProjectImage.JPG)

## 1. Character Data Acquisition 
I have downloaded the available specimen data made available to me by John C. Cisneros via messages on ResearchGate. This data matrix (originally formatted for TNT and Mesquite) was then input into IQTree to provide a TREE file. This tree file (of the phylogeny) was read using the ‘caper’ package’s “read.tree” command. The specimen data was read using the ‘caper’ package’s “read.nexus.data” command, and, after this, the data has to be converted into a data matrix to be used by this package and then I had to transpose it in order to have the data be read correctly by the “comparative.data” and “pgls” commands. 

## 2. Continent Data Acquisition 
I compiled the continent data from FossilWorks, a website that provides query, download, and analysis tools that utilize the Paleobiology Database 's large relational database assembled by hundreds of paleontologists from around the world. After gathering this data, I then created a file with the encoded continent data (located in the Github Repository).

## 3. Phylogenetic Generalized Least Squares (PGLS)
When interpreting these results, the “intercept” is the likelihood of a species from a specific area present labiolingual tooth broadening. The “intercept” in this coefficient table is, by default, the “0” value (which I have labeled as “Africa”), so the subsequent values (as.factor(GeoLoc)1, etc.) show the likelihood relative to the intercept (i.e. the “0” value, i.e. Africa). The slope shows the difference in likelihood between species of different continents presenting labiolingual tooth broadening or not presenting labiolingual tooth broadening. 

I used the command: “Geo.from.Max.Teeth <- pgls(as.numeric(V28) ~ as.factor(GeoLoc), cdat)” to examine the relationship between labiolingual tooth broadening and geographic location (continent).

There are no significant relationships to be reported, and there was no relationship identified between geographic location and whether or not teeth are labio-lingually broadened. 

# Discussion
As mentioned above, this study reports no significant relationships and that no relationship was identified between geographic location and whether or not teeth are labio-lingually broadened. My hypothesis was that, because there was a Triassic radiation of procolophonids, I would expect there to be lower association between procolophonids that exhibit vastly different tooth sizes and greater association between procolophonids that have similar tooth sizes (and therefore likely had similar diets and occupied similar niches). I reject my hypothesis in this study. 

The rightmost values (beneath “intercept”) in the coefficient table shown above are relative to the first “intercept” value (i.e. the “0” value, i.e. Africa). Instead of being a 50/50 reference point for the coefficients, we have -0.0596993 value which is close to 0. 

![Adjusted R.Squared](https://github.com/SelenaMart28/finalproject/blob/master/FinalProjectRMDAdjRsquared.JPG)

The adjusted R-squared value is -0.001568. This value is so low and indicates that this model (using geographic location to predict labiolingual tooth broadening ) is not good enough for predicting tooth morphology (labiolingual tooth broadening). I do not think this was an adequate coefficient of determination, as it predicts nowhere near 100% of the data. The negative, low value shows that this adjusted R-square value was negligible. Because of these results, I will conduct further analyses and attempt to find a variable (and its respective coefficient of determination) that may better explain the rapid radiation of procolophonids we see in the Triassic. 

I initially decided to go with an analysis using modern continents because my knowledge of previous environments, climates, etc. is not too developed. In the future, I would like to improve on this. Because of the time constraints I am facing currently, I failed to conduct a more extensive study of biogeographical regions and dental morphology. I plan to conduct a more in-depth study later this year. 

# Reflection

The biggest difficulty in implementing these analyses was gathering my data and determining what would make the most practical sense given the timeline of the course. Wrangling my data proved the most challenging and frustrating part of this project. Initially, I planned to use a character data matrix provided by Cisneros 2008, but the way the data matrix was uploaded made it near-unusable to use for recreating Cisneros' original analysis or using his data for further research. I reached out to Cisneros to obtain an actual usable file for my analysis. After this, I decided to try my hand at making my own data matrix (in the proper NEXUS, downloadable format), but I struggled to get IQTree (on the Cluster) to read my data. Eventually, my requests were answered! Cisneros messaged me with a usable file for my analysis and is the MatrixforEomurruna.nex file that I use in this project. I mention all of this because this difficulty in obtaining data from the literature showed me how important it is to leave data easily accessible and available for reproduction of research. It's integral to science!

If I did these analyses again, I would try to be better about outlining exactly what I wanted to do in this analysis and try to be better about what exactly I need to do to conduct this project. I would also try to be more proactive about seeking help (especially with the techinal R/coding portion of this project) earlier in the project. 

# References
- Blomberg S. P.,  Garland T.Jr.,  Ives A. R.. Testing for phylogenetic signal in comparative data: Behavioral traits are more labile, Evolution, 2003, vol. 57 (pg. 717-745)   (https://onlinelibrary.wiley.com/doi/epdf/10.1111/j.0014-3820.2003.tb00285.x).
- Botha Brink, Jennifer; Smith, Roger M. H. (2012). “Palaeobiology of Triassic procolophonids, inferred from bone microstructurePaleobiology of triassic procolophonids deduced from their bone microstructure”. Palevol Reviews 11. 419-433. (https://www.sciencedirect.com/science/article/pii/S1631068312000735).
- Cisneros, Juan C. (2008). “Phylogenetic relationships of procolophonid parareptiles with remarks on their geological record”. Journal of Systematic Palaeontology 6.
(https://www.tandfonline.com/doi/abs/10.1017/S1477201907002350).
- Cisneros, Juan C.; Ruta, Marcello (2010). “Morphological diversity and biogeography of procolophonids (Amniota: Parareptilia)”. Journal of Systematic Palaeontology (8). 		607-625. (https://www.researchgate.net/publication/233302378_Morphological_diversity_and_biogeography_of_procolophonids_Amniota_Parareptilia). 
- Dias-de-Silva, Sergio; Modesto, Sean P.; Schultz, Cesar L. (2006). “New material of Procolophon (Parareptilia: Procolophonoidea) from the Lower Triassic of Brazil, with remarks on the ages of the Sanga do Cabral and Buena Vista formations of South America”. Canadian Journal of Earth Sciences (43). 1685-1693.(https://www.nrcresearchpress.com/doi/abs/10.1139/e06-043#.X21CFj-Sk2w).
- Goloboff, P.A. and Catalano, S.A. (2016), TNT version 1.5, including a full implementation of phylogenetic morphometrics. Cladistics, 32: 221-238. doi:10.1111/cla.12160.
- Maddison DR, Swofford DL, Maddison WP. NEXUS: an extensible file format for systematic information. Syst Biol. 1997 Dec;46(4):590-621. (https://pubmed.ncbi.nlm.nih.gov/11975335/).
- Marshak, Stephen. (2019). Essentials of Geology. W W Norton. 
- Molina-Venegas, R., Rodríguez, M.Á. Revisiting phylogenetic signal; strong or negligible impacts of polytomies and branch length information?. BMC Evol Biol 17, 53 (2017). (https://bmcevolbiol.biomedcentral.com/articles/10.1186/s12862-017-0898-y#citeas).
- Münkemüller, T., Lavergne, S., Bzeznik, B., Dray, S., Jombart, T., Schiffers, K. and Thuiller, W. (2012), How to measure and test phylogenetic signal. Methods in Ecology and Evolution, 3: 743-756. (https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/j.2041-210X.2012.00196.x).
- Revell, L. J., Harmon, L. J., & Collar, D. C. (2008). Phylogenetic signal, evolutionary process, and rate. Systematic biology, 57(4), 591-601. (https://academic.oup.com/sysbio/article/57/4/591/1631730).
- Vaughan, T. G., IcyTree: Rapid browser-based visualization for phlogenetic trees and networks. Bioinformatics 2017. DOI: 10.1093/bioinformatics/btx155

