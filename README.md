#CAPÍTULO 1
##2.4.	 MATERIAL AND METHODS
###2.4.1.Comparative morphology
Multivariate analysis of variance (MANOVA) with a Canonical Variate Analysis (CVA).

Packages used `ggplot2` (Wickham 2016), `ggord` (Beck 2017) and `MASS` (Ripley *et al*. 2020).

Data available on my [Github](https://github.com/LucianoFBNeto/Tese_LucianoFBNeto).

```{r echo=FALSE}

#Open data
setwd("C:/Users/Luciano/Desktop/R_MarkDown")
data1=read.table("Data3.txt",header=TRUE)

```

```{r }
#Categorizing the data
data2=data1[,4:21]
quali=data1[,3]
```

```{r warning=FALSE}
#Open Packages
library(ggplot2)
library(ggord)
library(MASS)

```

```{r }
#Standardize the data
data3=scale(data2)

#Perform the CVA
cva=lda(data3, quali)

#Standard graphic of `ggplot2` package
ggord(cva, quali) 

#Graph with shape and color adjustments in `ggord` package
p <- ggord(cva, quali, poly = TRUE, ellipse=FALSE, hull=TRUE, polylntyp = quali, cols = c("#FF7F00","#1F78B4", "#B15928","#33A02C","#A6CEE3","#E31A1C"), size=3)
p + scale_shape_manual('Groups', values = c(25, 25, 25,6,25,25))
```


