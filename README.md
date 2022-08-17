# Analysis_of_single_cell_data_for_Usp22_project

The analysis pipeline can be run to reproduce the results of the scRNA-seq analysis in our manuscript.
Data required to run the analysis will be made available as soon as the manuscript is published.

The data were generated in two independent experiments. In each experiment samples of one wild type and one Usp22 knock-out mouse were processed. The provided code is designed to process data of the two experiments independently, so that genotypes are only compared within the same experiment. To process data of the two experiments consistently, some settings identified based on data from the first experiment (e.g. genes used for dimensionality reduction) are reused for processing data of the second experiment. Therefore, it is important to stick to this chronological order when reproducing the analysis.

One way to run the pipeline is to create a new R-project in RStudio using the Git option. When creating the R-project, specify the URL of our git repository to create a local copy in your R-project. After cloning the repository successfully, the whole pipeline can be executed by running the main.R script:
1. Open the main.R file and adjust the following settings:
    line 54: specifiy which replicate of the single-cell experiment you are analysing (1 or 2; start with 1)
    line 57, 60: specifiy if you want to save objects that are generated during the analysis (this can save you time if you need to rerun the     pipeline and protects you from loosing information if the pipeline breaks due to memory exhaustion)
    line 63: if you have already run the pipeline and you saved intermediate objects, you can use this option to reuse those objects to save      time.
    line 68: specify the location to which objects will be written.
    line 79-96: specifiy the paths to the input data (count matrices).
    line 101: specify the name of the folder in which plots will be saved.
2. Run the first section of the main.R file until all dependencies are installed and R is restarted.
3. Afterwards run the rest of the main.R script and the complete pipeline should be executed automatically.
4. Execute the pipeline a second time after specifying "replicate 2" in line 54.
5. You can now execute scripts which names start with "X_". Those script use objects generated by the pipeline. The script for processing the data from Camargo et al (DOI: 10.1038/nature25168) can be executed independent of generated objects.

Make sure that your computer remains connected to the internet while running the pipeline as some functions connect to databases.

known issue:
Sometimes the Biomart server is not available and therefore the cell annotation function fails. This issue should resolve when running the script at a later time.
