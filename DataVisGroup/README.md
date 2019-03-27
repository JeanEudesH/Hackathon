# README

This repository shows the process of the Data Visualization group and its results.

## Aim

Use the BrAPI calls implemented in OpenSILEX / PHIS to retrieve both environmental and phenotypic data and then display them in a responsive histogram.

For this purpose, we will test if it is possible to adapt the BrAPI-Graphical-Filtering BrAPP created by the BrAPI team : https://github.com/solgenomics/BrAPI-Graphical-Filtering

## Process step by step

1. Connect to GitHub and download the R app created by Jean-Eudes Hollebecq (optionnally, fork this repository) : https://github.com/OpenSILEX/opensilex-datavis-rapp-demo

```{bash}
git clone https://github.com/OpenSILEX/opensilex-datavis-rapp-demo.git
```

2. Change your directory name from "opensilex-datavis-rapp-demo" to something else (e.g. "hackathonApp")

3. Double-click on the .RProj file to open with RStudio the project you downloaded from GitHub

4. Install the packages necessary to communicate with OpenSILEX / PHIS Web Services :

```{r}
devtools::install_github("sanchezi/phisWSClientR", build_vignettes=TRUE) #"sanchezi/docAppPhisWSClientR"
devtools::install_github("OpenSILEX/opensilex-datavis-rapp-demo", build_vignettes=TRUE)
```

5. Initialize your connection with opensilex.org and get a token using the following R code :

```{r}
library(phisWSClientR)
initializeClientConnection(apiID="ws_private", url = "www.opensilex.org/openSilexAPI/rest/")
token <- getToken("guest@opensilex.org","guest")$data
```

6. Explore the **phisWSClientR** package functions :

```{r}
?phisWSClientR::getEnvironmentData
```

7. Explore the **compareVariableDemo** package (dowloaded from the OpenSILEX/opensilex-datavis-rapp-demo repository) functions :

```{r}
library(compareVariableDemo)
```

8. Change the *plotVarDemo.R* file using RStudio

9. Change the *getDF.R* file in order to get individual filters and remove the "chosen sensors" section

10. The variables of interest in our example are :

- LAI : http://www.opensilex.org/demo/id/variables/v001
- maximum wind speed : http://www.opensilex.org/demo/id/variables/v004

11. The changes made by Jean-Eudes are available in the GitHub repository he just created :

https://github.com/JeanEudesH/hackathonApp


