# Conformation_Analysis
Scripts used to perform calculations including embedding and clustering analysis.
## Package Requirements
- alabtools (https://github.com/alberlab/alabtools)
- pickle
- numpy
- scipy
- keras
- tensorflow
- sklearn
- matplotlib
- seaborn
## How to Run
Models generated by the Integrated Genome Modeling Platform (IGM) (https://github.com/alberlab/igm) (saved as for example GM_igm-model.hss) and partion files generated by the Markov Clustering Algorithm (MCL) (https://github.com/GuyAllard/markov_clustering) (saved as for example GM_speckle_clusters.dat) should be placed under directory Model/ for further usage. For the GM12878 model, please refer to https://doi.org/10.5281/zenodo.7352276. The spatial partition file of GM12878 and the genome populations of H1-hESC and HFFc6 are available at https://doi.org/10.5281/zenodo.7563402.

Script used to perform embedding:
```
python embedding.py <cell type> <chromosome index> <tag> <starting index> <ending index>
```
where "cell type" can be GM, H1 or HFF (GM for GM12878, H1 for H1-hESC and HFF for HFFc6), "chromosome index" should be ranging from 1 to 23 (1 to 22 for H1 or HFF), "tag" is 0 or 1 depends on whether autoencoder has been performed or not, "starting index" and "ending index" indicate the bead range. 

The following command line generate the embedding results for the whole chromosome 6 (bead index 0 to 854) of GM12878:
```
python embedding.py GM 6 0 0 855
```

Script used to perform clustering analysis:
```
python analysis.py <cell type> <chromosome index> <starting index> <ending index>
```
Similarly, we can run the analysis based on the results generated by the embedding:
```
python analysis.py GM 6 0 855
```
The results will be generated under directory GM_Structural_Features/. The speckle related calculations are only available for GM12878. To run the analysis without speckle related calculations for GM12878, H1-hESC or HFFc6:
```
python analysis_simple.py GM 6 0 855
```
The results will be generated under directory GM/.

