> [!NOTE]  
> Contains the code of the Tutorial-Section in<br>
> **Reconciling Latent Variables and Networks: Exploring and extending the Psychometric-Toolbox** [![arxiv badge](https://img.shields.io/badge/arXiv-2603.26116-red)](https://arxiv.org/abs/2603.26116)

```bibtex
@unpublished{Kistermann.2026.prePrint,
 author = {Kistermann, Kevin and Andriamiarana, Vivato V. and Kelava, Augustin},
 year = {2026},
 title = {Reconciling Latent Variables and Networks: Exploring and extending the Psychometric-Toolbox},
 url = {https://arxiv.org/pdf/2603.26116},
 note = {Preprint}
}
```

# Utilize your Tools (Tutorials)

In this Tutorial-Section three methods (mlVAR, GIMME, and Recurrence Analysis) are applied to a psychometric ILD dataset from [Rowland & Wenzel (2020)](https://doi.org/10.1007/s12671-020-01335-4).
```bibtex
@article{Rowland.2020.Dataset,
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
```

Consisting of of 125 undergraduate students (M age = 22.87; SD = 5.06 years; 77.6% female) who answered eight items assess ing their affective experiences ("happy", "excited", "relaxed", "satisfied", "angry", "anxious", "depressed", "sad") on a visual slider scale from 0 (not at all) to 100 (very much), 6 times a day for 40 days, and were either randomly selected for a weekly mindfulness training (n=61) or a wait list control condition (n=64).

> [!NOTE]  
> `data_affect.csv` available at https://osf.io/jmz2n/overview<br>
> see [data_README.pdf](data_README.pdf) for detailed informaiton about the dataset.


## 1. Multi-Level Vector Autoregression (mlVAR) [mlVAR_GIMME.Rmd](mlVAR_GIMME.Rmd)
```bibtex
@article{Epskamp.2018.GGM-GVAR,
 author = {Epskamp, Sacha and Waldorp, Lourens J. and M{\~o}ttus, Ren{\'e} and Borsboom, Denny},
 year = {2018},
 title = {{The Gaussian Graphical Model in Cross-Sectional and Time-Series Data}},
 pages = {453--480},
 volume = {53},
 number = {4},
 journal = {{Multivariate Behavioral Research}},
 doi = {10.1080/00273171.2018.1454823}
}
```
The multilevel VAR (mlVAR; [Epskamp, Waldorp, et al., 2018](https://www.tandfonline.com/doi/full/10.1080/00273171.2018.1454823)) models each person with an individual gVAR model. Two estimation methods are implemented in R-Packages, the _pooled and individual LASSO estimation_ with `mlGraphicalVAR()` in [![R-Package: mlVAR](https://img.shields.io/badge/R--Package-graphicalVAR-blue)](https://cran.r-project.org/web/packages/graphicalVAR/index.html) and used in the original analy sis of [Rowland & Wenzel (2020)](https://doi.org/10.1007/s12671-020-01335-4), and the _two step frequentist multilevel_ approach which is im plemented with `mlVAR()` in [![R-Package: mlVAR](https://img.shields.io/badge/R--Package-mlVAR-blue)](https://cran.r-project.org/web/packages/mlVAR/index.html). 

```r
library(mlVAR)

#estimating mlVAR model
mlvar_group1 <- mlVAR(data_group1, 
                     vars = variables,
                     idvar = "subjno",
                     lags = 1, 
                     dayvar = "dayno", 
                     beepvar = "beep")

mlvar_group2 <- mlVAR(data_group2, 
                     vars = variables,
                     idvar = "subjno",
                     lags = 1, 
                     dayvar = "dayno", 
                     beepvar = "beep")


# generate Figure 9 in Publication
jpeg("figure_mlVAR.jpg", width = 1500, height = 2000, res = 300)
layout(matrix(1:6, nrow = 3, ncol = 2, byrow = TRUE))

plot(mlvar_group1, "temporal", title = "temporal (A)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)
plot(mlvar_group2, "temporal", title = "temporal (B)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)


plot(mlvar_group1, "contemporaneous", title = "contemporaneous (A)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)
plot(mlvar_group2, "contemporaneous", title = "contemporaneous (B)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)

plot(mlvar_group1, "between", title = "between (A)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)
plot(mlvar_group2, "between", title = "between (B)", layout = "circle", nonsig = "hide", theme = "gray", vsize = 13)
```
<p align="center">
  <img src="figures/figure_mlVAR.jpg" width="700"/>
  <br>
  <em>Figure 9: mlVAR(...) output plotted. With control group (A) and intervention group (B). Edges in the within person contemporaneous and between-person network are partial-correlations, in the within-person temporal networks lag-1 autoregressive coefficients. Shading and width indicate edge strength, with positive values (solid) and negative values (dashed).</em>
</p>


**Differences between control and intervention group seem to be small, at least when plotting the aggregated network for all individuals of both groups. Networks of individuals can be plotted as well, here more pronounced differences in network topology can be spotted. This suggest that analyzing and plotting aggregated networks might be of limited use, even though it is often the default in empirical research.**

```r
# random sample of people
subjects <- c(10, 17, 36, 55, 84, 109)

# plot + save all figures
for (s in subjects) {
    plot(mlvar_all, "temporal",
       title = paste0("temporal network of subject ", s),
       subject = s,
       layout = "circle"
       )
}
```

<p align="center">
 <img src="figures/figure_temporal_network_10.jpg" width="45%"/>
 <img src="figures/figure_temporal_network_17.jpg" width="45%"/>
 <img src="figures/figure_temporal_network_36.jpg" width="45%"/>
 <img src="figures/figure_temporal_network_55.jpg" width="45%"/>
 <img src="figures/figure_temporal_network_84.jpg" width="45%"/>
 <img src="figures/figure_temporal_network_109.jpg" width="45%"/>
 <br>
 <em>Green edges indicate positive weights and red edges indicate negative weights.</em>
</p>





```r
# plot + save all figures
for (s in subjects) {
  plot(mlvar_all, "contemporaneous",
       title = paste0("contemporaneous network of subject ", s),
       subject = s,
       layout = "circle"
       )
}
```
<p align="center">
 <img src="figures/figure_contemporaneous_network_10.jpg" width="45%"/>
 <img src="figures/figure_contemporaneous_network_17.jpg" width="45%"/>
 <img src="figures/figure_contemporaneous_network_36.jpg" width="45%"/>
 <img src="figures/figure_contemporaneous_network_55.jpg" width="45%"/>
 <img src="figures/figure_contemporaneous_network_84.jpg" width="45%"/>
 <img src="figures/figure_contemporaneous_network_109.jpg" width="45%"/>
 <br>
 <em>Green edges indicate positive weights and red edges indicate negative weights.</em>
</p>

### Other Tutorial:   
- https://quantdev.ssri.psu.edu/sites/qdev/files/APA-ATI_ILD_Session_R_-_Multivariate_Dynamics_and_Networks.html





## 2. Group Iterative Multiple Model Estimation (GIMME) in [mlVAR_GIMME.Rmd](mlVAR_GIMME.Rmd)
[![R-Package: mlVAR](https://img.shields.io/badge/R--Package-gimme-blue)](https://cran.r-project.org/web/packages/gimme/index.html)
```bibtex
@article{Gates.2012.GIMME,
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
 author = {Beltz, Adriene M. and Wright, Aidan G. C. and Sprague, Briana N. and Molenaar, Peter C. M.},
 year = {2016},
 title = {{Bridging the Nomothetic and Idiographic Approaches to the Analysis of Clinical Data}},
 pages = {447--458},
 volume = {23},
 number = {4},
 journal = {Assessment},
 doi = {10.1177/1073191116648209 }
}

@article{Gates.2017.S-GIMME,
 author = {Gates, Kathleen M. and Lane, Stephanie T. and Varangis, E. and Giovanello, K. and Guskiewicz, K.},
 year = {2017},
 title = {Unsupervised Classification During Time-Series Model Building},
 keywords = {Model(s) - GIMME},
 pages = {129--148},
 volume = {52},
 number = {2},
 journal = {{Multivariate Behavioral Research}},
 doi = {10.1080/00273171.2016.1256187}
}

```
### Estimate a GIMME for Group 1 (control)

```r
data_GIMME_1 <- data_group1 %>%
  group_by(subjno) %>%
  group_split() %>%
  lapply(function(df) 
    {df %>%
      select(-subjno, -dayno, -beep, -group) %>% # remove all columns that are not variables
      as.data.frame() # gimme prefers base data.frames
      })

GIMME <- gimme(data = data_GIMME_1)

plot(GIMME)
```
<p align="center">
  <img src="figures/figure_GIMME_control.jpg" width="700"/>
  <br>
  <em>?</em>
</p>

```r
# plot random sample of individual networks
plot(GIMME$plots$subj4)
plot(GIMME$plots$subj17)
plot(GIMME$plots$subj52)
plot(GIMME$plots$subj62)
plot(GIMME$plots$subj36)
plot(GIMME$plots$subj53)
```

<p align="center">
 <img src="figures/figure_GIMME_control_individuals.jpg" width="45%"/>
 <br>
 <em>?</em>
</p>


### Estimate a GIMME for Group 2 (intervention)
```r
GIMME_2 <- gimme(data = data_GIMME_2)

plot(GIMME_2)
```
<p align="center">
  <img src="figures/figure_GIMME_intervention.jpg" width="700"/>
  <br>
  <em>?</em>
</p>

```r
# plot random sample of individual networks
plot(GIMME_2$plots$subj1)
plot(GIMME_2$plots$subj31)
plot(GIMME_2$plots$subj51)
plot(GIMME_2$plots$subj57)
plot(GIMME_2$plots$subj16)
plot(GIMME_2$plots$subj27)
```

<p align="center">
 <img src="figures/figure_GIMME_intervention_individuals.jpg" width="45%"/>
 <br>
 <em>?</em>
</p>

### S-GIMME
```r
library(gimme)

S_GIMME <- gimme(data        = data_GIMME, 
                 subgroup    = TRUE,
                 sub_feature = "lag & contemp", 
                 sub_method  = "Walktrap", 
                 groupcutoff = .75, 
                 subcutoff   = .75)

plot(S_GIMME)

# generate Figure
jpeg("S-GIMME.jpg", width = 1000, height = 1000, res = 300)
plot(S_GIMME)
dev.off()
```

<p align="center">
  <img src="figures/figure_S-GIMME.jpg" width="700"/>
  <br>
  <em>?</em>
</p>



### Other Turorials:  
- https://tarheels.live/gimme/tutorials/  
- https://andysbrainbook.readthedocs.io/en/latest/Statistics/GIMME.html  
- https://cran.r-project.org/web/packages/gimme/vignettes/gimme_vignette.html  


## 3. Recurrence Plot (in [RecurrenceAnalysis.ipynb](RecurrenceAnalysis.ipynb))

[![python: pyunicorn](https://img.shields.io/badge/python-pyunicorn-green)](https://www.pik-potsdam.de/~donges/pyunicorn)

```bibtex
@article{Donges.2015.pyunicorn,
 author = {Donges, Jonathan F. and Heitzig, Jobst and Beronov, Boyan and Wiedermann, Marc and Runge, Jakob and Feng, Qing Yi and Tupikina, Liubov and Stolbova, Veronika and Donner, Reik V. and Marwan, Norbert and Dijkstra, Henk A. and Kurths, J{\"u}rgen},
 year = {2015},
 title = {Unified functional network and nonlinear time series analysis for complex systems science: The pyunicorn package},
 pages = {113101},
 volume = {25},
 number = {11},
 journal = {Chaos},
 doi = {10.1063/1.4934554}
}
```


```python
from pyunicorn.timeseries import RecurrencePlot
import numpy as np
import matplotlib.pyplot as plt

# select the person
person = 120

df_person = df[df["subjno"] == person] # filter the df for a specific person

df_person = df_person.iloc[:, -8:] # only keep the variable columns

# rename the columns
df_person.columns = (
    "happy",
    "excited",
    "relaxed",
    "satisfied",
    "angry",
    "anxious",
    "depressed",
    "sad",
)
#remove rows with NaN values --> which is ok to do because "the concept of recurrence plots does not require observations that are equally spaced in time."?
df_person = df_person.dropna() 


# https://www.pik-potsdam.de/~donges/pyunicorn/api/timeseries/recurrence_plot.html
# metric = "manhattan", "euclidean", or "supremum"
RecPlo = RecurrencePlot(df_person.to_numpy(), metric="euclidean", normalize=True, threshold=0.7) # .to_numpy() because we imported a pandas df, but we need a numpy array

stats = RecPlo.rqa_summary() #some summary statistics of the Recurrence Plot



plt.matshow(np.tril(RecPlo.recurrence_matrix()) , origin='lower', cmap="binary")
plt.ylabel("$t$")
plt.xticks(np.arange(0, len(df_person), 20))
plt.yticks(np.arange(0, len(df_person), 20))

txt = "\n".join(f"{k} = {v:.2f}" for k, v in stats.items())
plt.text(0.75, 0.2, txt, transform=plt.gca().transAxes,
    va="top",
    bbox=dict(facecolor="white", alpha=0.8)
)

plt.show()

```

<p align="center">
  <img src="figures/figure_recurrence_plot_person_120.jpg" width="700"/>
  <br>
  <em>?</em>
</p>




### Other resources:
- https://www.pik-potsdam.de/~donges/pyunicorn/examples/tutorials/RecurrenceNetworks.html
- https://complexity-methods.github.io/book/lvSystem.html
- http://www.recurrence-plot.tk
- https://mathworld.wolfram.com/RecurrencePlot.html
- https://heinonmatti.github.io/complexity-behchange/Recurrence-plots.html


# IMPS 2026 Poster [![DOI](https://zenodo.org/badge/1235487433.svg)](https://doi.org/10.5281/zenodo.21129486)
<p align="center">
  <img src="figures/IMPS26_Poster_A0.jpg" width="700"/>
</p>

