# Phylogenetic Biology - Final Project

## Guidelines - you can delete this section before submission

This repository is a stub for your final project. Fork it, develop your project, and submit it as a pull request. Edit/ delete the text in this readme as needed.

Some guidelines and tips:

- Use the stubs below to write up your final project. Alternatively, if you would like the writeup to be an executable document (with [knitr](http://yihui.name/knitr/), [jupytr](http://jupyter.org/), or other tools), you can create it as a separate file and put a link to it here in the readme.

- For information on formatting text files with markdown, see https://guides.github.com/features/mastering-markdown/ . You can use markdown to include images in this document by linking to files in the repository, eg `![GitHub Logo](/images/logo.png)`.

- The project must be entirely reproducible. In addition to the results, the repository must include all the data (or links to data) and code needed to reproduce the results.

- If you are working with unpublished data that you would prefer not to publicly share at this time, please contact me to discuss options. In most cases, the data can be anonymized in a way that putting them in a public repo does not compromise your other goals.

- Paste references (including urls) into the reference section, and cite them with the general format (Smith at al. 2003).

- Commit and push often as you work.

OK, here we go.

# Title of my project

## Introduction and Goals

The goal of my project is to answer the following question: are procolophonids that have similar tooth sizes more closely related to one another than procolophonids with differing tooth sizes? I am interested to see if more closely related procolophonids may have more similar diets and lifestyles.

For this project, I will compare the various dentitions of procolophonids, an extinct clade of anapsid reptiles that lived during the late Permian through the Triassic (~300-200 million years ago). Procolophonids are the only clade within the larger clade Parareptilia to survive the Permo-Triassic mass extinction, the most devastating mass extinction to occur in earth’s history (Essentials of Geology). Procolophonids are a large and successful group of parareptiles with more than 30 known genera (Cisneros, 2008). They occupied a wide geographic range, including the Americas, Europe, Asia, Africa, and Antarctica (Dias-de-Silva, Modesto and Schultz, 2006; Cisneros and Ruta, 2010). Research has shown that procolophonids likely had a fossorial (burrowing) lifestyle, feeding on insects and plants (Botha-Brink and Smith, 2012). Most researchers think procolophonids are herbivorous or durophagous, but there no full analysis of procolophonid teeth has been done in relation to their places on the tree of life. 

The methods I will use to do this include phylogenetic signal analysis, specifically by employing the method outlined by Blomberg et al, 2003. 
Using the concept of phylogenetic covariance, I will determine if similarities in dentition between species of procolophonids can be attributed to their shared history or if another factor is responsible for these similarities (Revell, Harmon, and Collar, 2008). In this analysis, I will place the traits at their respective tips on the tree, and then run a phylogenetic signal analysis to determine a K value for comparison among pairs of procolophonids. Additionally, I will evaluate Pagel's lambda to measure and test phylogenetic signal (Molina-Venegas and Rodriguez, 2017). The tree I will be using is taken from Cisneros' 2008 paper on procolophonid phylogeny, though I will be removing taxa for which I do not have tooth area values. 

The data I will use is my own, collected as part of a survey of published research with occlusal views of procolophonid dentition. To conduct the initial phylogenetic inference, I will be using traits detailed in John. C Cisneros' 2008 paper on procolophonid phylogeny and using this tree (and the traits) to perform a phylogenetic signal analysis based on dentition. 


Because I suspect that there was a Triassic radiation of procolophonids, I would expect there to be lower covariance values between procolophonids that exhibit vastly different tooth sizes and greater covariance values between procolophonids that have similar tooth sizes (and therefore likely had similar diets and occupied similar niches). 

## Methods

The tools I used were... 

## Results

The tree in Figure 1...

## Discussion

These results indicate...

The biggest difficulty in implementing these analyses was...

If I did these analyses again, I would...

## References
- Blomberg S. P.,  Garland T.Jr.,  Ives A. R.. Testing for phylogenetic signal in comparative data: Behavioral traits are more labile, Evolution, 2003, vol. 57 (pg. 717-745)   (https://onlinelibrary.wiley.com/doi/epdf/10.1111/j.0014-3820.2003.tb00285.x).
- Botha Brink, Jennifer; Smith, Roger M. H. (2012). “Palaeobiology of Triassic procolophonids, inferred from bone microstructurePaleobiology of triassic procolophonids deduced from their bone microstructure”. Palevol Reviews 11. 419-433. (https://www.sciencedirect.com/science/article/pii/S1631068312000735).
- Cisneros, Juan C. (2008). “Phylogenetic relationships of procolophonid parareptiles with remarks on their geological record”. Journal of Systematic Palaeontology 6.
(https://www.tandfonline.com/doi/abs/10.1017/S1477201907002350).
- Cisneros, Juan C.; Ruta, Marcello (2010). “Morphological diversity and biogeography of procolophonids (Amniota: Parareptilia)”. Journal of Systematic Palaeontology (8). 		607-625. (https://www.researchgate.net/publication/233302378_Morphological_diversity_and_biogeography_of_procolophonids_Amniota_Parareptilia). 
- Dias-de-Silva, Sergio; Modesto, Sean P.; Schultz, Cesar L. (2006). “New material of Procolophon (Parareptilia: Procolophonoidea) from the Lower Triassic of Brazil, with remarks on the ages of the Sanga do Cabral and Buena Vista formations of South America”. Canadian Journal of Earth Sciences (43). 1685-1693.(https://www.nrcresearchpress.com/doi/abs/10.1139/e06-043#.X21CFj-Sk2w).
- Marshak, Stephen. (2019). Essentials of Geology. W W Norton. 
- Molina-Venegas, R., Rodríguez, M.Á. Revisiting phylogenetic signal; strong or negligible impacts of polytomies and branch length information?. BMC Evol Biol 17, 53 (2017). (https://bmcevolbiol.biomedcentral.com/articles/10.1186/s12862-017-0898-y#citeas).
- Revell, L. J., Harmon, L. J., & Collar, D. C. (2008). Phylogenetic signal, evolutionary process, and rate. Systematic biology, 57(4), 591-601. (https://academic.oup.com/sysbio/article/57/4/591/1631730).

