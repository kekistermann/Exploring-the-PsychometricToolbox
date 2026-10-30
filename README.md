# Reconciling latent variables and networks: Exploring and extending the Psychometric-Toolbox
prePrint: https://arxiv.org/abs/2603.26116

## Utilize your Tools (Tutorials)
### Data: 

data_affect.csv \& data_net_density.csv --> https://osf.io/jmz2n/overview

@article{Rowland.2016.Dataset,
 author = {Rowland, Zarah and Wenzel, Mario and Kubiak, Thomas},
 year = {2016},
 title = {The effects of computer-based mindfulness training on Self-control and Mindfulness within Ambulatorily assessed network Systems across Health-related domains in a healthy student population (SMASH): study protocol for a randomized controlled trial},
 pages = {570},
 volume = {17},
 number = {1},
 journal = {Trials},
 doi = {10.1186/s13063-016-1707-4}
}

@article{Rowland.2019.Dataset,
 author = {Rowland, Zarah and Wenzel, Mario and Kubiak, Thomas},
 year = {2019},
 title = {Effects of an Ultra-brief Computer-based Mindfulness Training on Mindfulness and Self-control: a Randomised Controlled Trial Using a 40-Day Ecological Momentary Assessment},
 pages = {2312--2326},
 volume = {10},
 number = {11},
 issn = {1868-8527},
 journal = {Mindfulness},
 doi = {10.1007/s12671-019-01204-9}
}

@article{Rowland.2020a.Dataset,
 author = {Rowland, Zarah and Wenzel, Mario and Kubiak, Thomas},
 year = {2020},
 title = {A mind full of happiness: How mindfulness shapes affect dynamics in daily life},
 pages = {436--451},
 volume = {20},
 number = {3},
 issn = {1528-3542},
 journal = {Emotion},
 doi = {10.1037/emo0000562}
}

@article{Rowland.2020b.Dataset,
 author = {Rowland, Zarah and Wenzel, Mario},
 year = {2020},
 title = {Mindfulness and Affect-Network Density: Does Mindfulness Facilitate Disengagement from Affective Experiences in Daily Life?},
 pages = {1253--1266},
 volume = {11},
 number = {5},
 issn = {1868-8527},
 journal = {Mindfulness},
 doi = {10.1007/s12671-020-01335-4}
}


###  mlVAR_GIMME.Rmd
#### 1. mlVAR
@article{Epskamp.2018.GMM-GVAR,
author = {Epskamp, Sacha and Waldorp, Lourens J. and M?ttus, Ren? and Borsboom, Denny},
title = {The Gaussian Graphical Model in Cross-Sectional and Time-Series Data},
journal = {Multivariate Behavioral Research},
volume = {53},
number = {4},
pages = {453--480},
year = {2018},
publisher = {Routledge},
doi = {10.1080/00273171.2018.1454823}   
}
also: https://arxiv.org/abs/1609.04156

Other Tutorial:   
- https://quantdev.ssri.psu.edu/sites/qdev/files/APA-ATI_ILD_Session_R_-_Multivariate_Dynamics_and_Networks.html


#### 2. GIMME

@article{Gates.2012.GIMME,
 abstract = {At its best, connectivity mapping can offer researchers great insight into how spatially disparate regions of the human brain coordinate activity during brain processing. A recent investigation conducted by Smith and colleagues (2011) on methods for estimating connectivity maps suggested that those which attempt to ascertain the direction of influence among ROIs rarely provide reliable results. Another problem gaining increasing attention is heterogeneity in connectivity maps. Most group-level methods require that the data come from homogeneous samples, and misleading findings may arise from current methods if the connectivity maps for individuals vary across the sample (which is likely the case). The utility of maps resulting from effective connectivity on the individual or group levels is thus diminished because they do not accurately inform researchers. The present paper introduces a novel estimation technique for fMRI researchers, Group Iterative Multiple Model Estimation (GIMME), which demonstrates that using information across individuals assists in the recovery of the existence of connections among ROIs used by Smith and colleagues (2011) and the direction of the influence. Using heterogeneous in-house data, we demonstrate that GIMME offers a unique improvement over current approaches by arriving at reliable group and individual structures even when the data are highly heterogeneous across individuals comprising the group. An added benefit of GIMME is that it obtains reliable connectivity map estimates equally well using the data from resting state, block, or event-related designs. GIMME provides researchers with a powerful, flexible tool for identifying directed connectivity maps at the group and individual levels.},
 author = {Gates, Kathleen M. and Molenaar, Peter C. M.},
 year = {2012},
 title = {Group search algorithm recovers effective connectivity maps for individuals in homogeneous and heterogeneous samples},
 pages = {310--319},
 volume = {63},
 number = {1},
 journal = {NeuroImage},
 doi = {10.1016/j.neuroimage.2012.06.026}
}

@article{Beltz.2016.GIMME,
 abstract = {The nomothetic approach (i.e., the study of interindividual variation) dominates analyses of clinical data, even though its assumption of homogeneity across people and time is often violated. The idiographic approach (i.e., the study of intraindividual variation) is best suited for analyses of heterogeneous clinical data, but its person-specific methods and results have been criticized as unwieldy. Group iterative multiple model estimation (GIMME) combines the assets of the nomothetic and idiographic approaches by creating person-specific maps that contain a group-level structure. The maps show how intensively measured variables predict and are predicted by each other at different time scales. In this article, GIMME is introduced conceptually and mathematically, and then applied to an empirical data set containing the negative affect, detachment, disinhibition, and hostility composite ratings from the daily diaries of 25 individuals with personality pathology. Results are discussed with the aim of elucidating GIMME's potential for clinical research and practice.},
 author = {Beltz, Adriene M. and Wright, Aidan G. C. and Sprague, Briana N. and Molenaar, Peter C. M.},
 year = {2016},
 title = {Bridging the Nomothetic and Idiographic Approaches to the Analysis of Clinical Data},
 pages = {447--458},
 volume = {23},
 number = {4},
 journal = {Assessment},
 doi = {10.1177/1073191116648209 }
}

@article{Gates.2017.S-GIMME,
 abstract = {Researchers who collect multivariate time-series data across individuals must decide whether to model the dynamic processes at the individual level or at the group level. A recent innovation, group iterative multiple model estimation (GIMME), offers one solution to this dichotomy by identifying group-level time-series models in a data-driven manner while also reliably recovering individual-level patterns of dynamic effects. GIMME is unique in that it does not assume homogeneity in processes across individuals in terms of the patterns or weights of temporal effects. However, it can be difficult to make inferences from the nuances in varied individual-level patterns. The present article introduces an algorithm that arrives at subgroups of individuals that have similar dynamic models. Importantly, the researcher does not need to decide the number of subgroups. The final models contain reliable group-, subgroup-, and individual-level patterns that enable generalizable inferences, subgroups of individuals with shared model features, and individual-level patterns and estimates. We show that integrating community detection into the GIMME algorithm improves upon current standards in two important ways: (1) providing reliable classification and (2) increasing the reliability in the recovery of individual-level effects. We demonstrate this method on functional MRI from a sample of former American football players.},
 author = {Gates, Kathleen M. and Lane, Stephanie T. and Varangis, E. and Giovanello, K. and Guskiewicz, K.},
 year = {2017},
 title = {Unsupervised Classification During Time-Series Model Building},
 keywords = {Model(s) - GIMME},
 pages = {129--148},
 volume = {52},
 number = {2},
 journal = {Multivariate behavioral research},
 doi = {10.1080/00273171.2016.1256187}
}




Other Resources:  
- https://tarheels.live/gimme/tutorials/  
- https://andysbrainbook.readthedocs.io/en/latest/Statistics/GIMME.html  
- https://cran.r-project.org/web/packages/gimme/vignettes/gimme_vignette.html  


### RecurrenceAnalysis.ipynb
#### 3. Recurrence Analysis

https://www.pik-potsdam.de/~donges/pyunicorn/index.html

Tutorial: https://www.pik-potsdam.de/~donges/pyunicorn/examples/tutorials/RecurrenceNetworks.html


@article{Donges.2015.pyunicorn,
 abstract = {We introduce the pyunicorn (Pythonic unified complex network and recurrence analysis toolbox) open source software package for applying and combining modern methods of data analysis and modeling from complex network theory and nonlinear time series analysis. pyunicorn is a fully object-oriented and easily parallelizable package written in the language Python. It allows for the construction of functional networks such as climate networks in climatology or functional brain networks in neuroscience representing the structure of statistical interrelationships in large data sets of time series and, subsequently, investigating this structure using advanced methods of complex network theory such as measures and models for spatial networks, networks of interacting networks, node-weighted statistics, or network surrogates. Additionally, pyunicorn provides insights into the nonlinear dynamics of complex systems as recorded in uni- and multivariate time series from a non-traditional perspective by means of recurrence quantification analysis, recurrence networks, visibility graphs, and construction of surrogate time series. The range of possible applications of the library is outlined, drawing on several examples mainly from the field of climatology.},
 author = {Donges, Jonathan F. and Heitzig, Jobst and Beronov, Boyan and Wiedermann, Marc and Runge, Jakob and Feng, Qing Yi and Tupikina, Liubov and Stolbova, Veronika and Donner, Reik V. and Marwan, Norbert and Dijkstra, Henk A. and Kurths, J{\"u}rgen},
 year = {2015},
 title = {Unified functional network and nonlinear time series analysis for complex systems science: The pyunicorn package},
 pages = {113101},
 volume = {25},
 number = {11},
 journal = {Chaos},
 doi = {10.1063/1.4934554}
}
--> https://arxiv.org/pdf/1507.01571



Other resources:
- https://complexity-methods.github.io/book/lvSystem.html
- http://www.recurrence-plot.tk
- https://mathworld.wolfram.com/RecurrencePlot.html
- https://heinonmatti.github.io/complexity-behchange/Recurrence-plots.html


# IMPS 2026 Poster
