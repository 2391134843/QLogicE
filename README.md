# The Model QLogicE

This repository is the implementation codes for the model `QLogicE`. This model joints the translation embedding `TransE` and the quantum logic `E2R` for the sake of capturing more features to improve the expressiveness of the knowledge graph completion task. 
## Download the Code 

Firstly, the code can be cloned from the github repository by following command:
```
git clone https://github.com/gzupanda/QLogicE.git
```
The code mainly depends on `PyTorch 1.1.0` or later versions and `Python 3` which is modified from the baseline model [E2R](https://github.com/IBM/e2r). In this code, there are seven directories corresponding to each dataset. 

## Datasets for Evalating the Model
The datasets used in our experiments are as follows.

|Dataset|Entity|Relation|Train|Valid|Test|Triples|
|-------|------|--------|-----|-----|----|-------|
|Kinship|104|26|8,544|1,068|1,074|10,686|
|UMLS|135|49|5,216|652|661|6,529|
|FB15k|14,951|1,345|483,142|50,000|59,071|592,213|
|WN18|40,943|18|141,442|5,000|5,000|151,442|
|FB15k237|14,505|237|272,115|17,535|20,466|310,116|
|WN18RR|40,943|11|86,835|3,034|3,134|93,003|
|YAGO3-10|123,182|37|1,079,040|5,000|5,000|1,089,040|

In other words, every directory is an independent one with the data such as training, validing testing and trained model data. Besides, there are codes including data parser, training, testing, evaluating, etc. To better understand how to quick start to run the experiments, we take the dataset `UMLS` for example.
## Run the Experiments
There are seven directories in this repository corresponding the seven datasets. They are devided as three groups, . Fortunately, the running is simple. For every dataset, we just run the following steps and take the dataset `umls` for example:
### 1. Enter the Directory
In every directory, there are eight python files and two directories. We can go into the objective directory to run the right codes. In this case, it is the directory `unls`.
```
cd QLogicE
cd umls
```
### 2. Training the Model
When we finish the above step, we can run the following command to training the dataset. And the trained model is saved in the directory save. In this case, it is the dataset `UMLS`.
```
python Train.py
```
### 3. Testing the Model
In this step, the code is used for test the training results. We only need to run the followinng command.
```
python Test.py
```

|Model|FB15k|FB15k|FB15k|WN18|WN18|WN18|FB15k237|FB15k237|FB15k237|WN18RR|WN18RR|WN18RR|YAGO3-10|YAGO3-10|YAGO3-10|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10|
TransE|0.628|49.36|84.73|0.646|40.56|94.87|0.310|21.72|49.65|0.206|2.79|49.52|0.501|40.57|67.39|
|E2R|0.964|96.40|96.40|0.710|71.10|71.10|0.584|58.40|58.40|0.477|47.70|47.70|0.830|83.00|83.00|
|QLogicE|0.969|96.93|96.93|0.927|92.70|92.70|0.949|94.89|94.89|0.928|92.79|92.79|0.937|93.74|93.74|

## Performance of the Results
In this model, the proposed model achieves outstanding results, especially on the challenging datasets such as `FB15k237`, `WN18RR` and `YAGO3-10`.

|Model|FB15k|FB15k|FB15k|WN18|WN18|WN18|FB15k237|FB15k237|FB15k237|WN18RR|WN18RR|WN18RR|YAGO3-10|YAGO3-10|YAGO3-10|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10| MRR| Hits@1| Hits@10|
|ConvE|0.688|59.46|84.94|0.945|93.89|95.68|0.305|21.90|47.62|0.427|38.99|50.75|0.488|39.93|65.75|
|ConvKB|0.211|11.44|40.83|0.709|52.89|94.89|0.230|13.98|41.46|0.249|5.63|52.50|0.420|32.16|60.47|
|ConvR|0.773|70.57|88.55|0.950|94.56$|95.85|0.346|25.56|52.63|0.467|43.73|52.68|0.527|44.62|67.33|
|CapsE|0.087|1.934|21.78|0.890|84.55|95.08|0.160|7.34|35.60|0.415|33.69|55.98|0.000|0.00|0.00|
|RSN|0.777|72.34|87.01|0.928|91.23|95.10|0.280|19.84|44.44|0.395|34.59|48.34|0.511|42.65|66.43|
|TransE|0.628|49.36|84.73|0.646|40.56|94.87|0.310|21.72|49.65|0.206|2.79|49.52|0.501|40.57|67.39|
|STransE|0.543|39.77|79.60|0.656|43.12|93.45|0.315|22.48|49.56|0.226|10.13|42.21|0.049|3.28|7.35|
|CrossE|0.702|60.08|86.23|0.834|73.28|95.03|0.298|21.21|47.05|0.405|38.07|44.99|0.446|33.09|65.45|
|TorusE|0.746|68.85|83.98|0.947|94.33|95.44|0.281|19.62|44.71|0.463|42.68|53.35|0.342|27.43|47.44|
|RotatE|0.791|73.93|88.10|0.949|94.43|96.02|0.336|23.83|53.06|0.475|42.60|57.35|0.498|40.52|67.07|
|DistMult|0.784|73.68|86.32|0.824|72.60|94.61|0.313|22.44|49.01|0.433|39.68|50.22|0.501|41.26|66.12|
|ComplEx|0.848|81.56|90.53|0.949|94.53|95.50|0.349|25.72|52.97|0.458|42.55|52.12|0.576|50.48|70.35|
|Analogy|0.726|65.59|83.74|0.934|92.61|94.42|0.202|12.59|35.38|0.366|35.82|38.00|0.283|19.21|45.65|
|SimplE|0.726|66.13|83.63|0.938|93.25|94.58|0.179|10.03|34.35|0.398|38.27|42.65|0.453|35.76|63.16|
|HolE|0.800|75.85|86.78|0.938|93.11|94.94|0.303|21.37|47.64|0.432|40.28|48.79|0.502|41.84|65.19|
|TuckER|0.788|72.89|88.88|0.951|94.64|95.80|0.352|25.90|53.61|0.459|42.95|51.40|0.544|46.56|68.09|
|QLogicE|0.969|96.93|96.93|0.914|91.42|91.42|0.949|94.89|94.89|0.928|92.79|92.79|0.937|93.74|93.74|

From this table, we can see that the proposed model `QLogicE` achieves the state-of-the-art over the existing models. Notably, the performance on dateset `WN18` is not as promsing as the models achieved, though the model achieve the outstanding performance on other datasets such as `FB15k`, `FB15k237` and `WN18RR`. Fortunately, these performance results are better than the baseline model `E2R` with large margin on dataset `WN18`. The ablation performance results show this point.

From this table, it can be seen that the proposed model significant better than the baselines model on datasets except `WN18`.
## The Dense Feature Model
Inspired by the surprising performance of the model `QLogicE`, we coformulate a dense feature model framework from the perspective of information theory to guide the further knowledge graph completion model design. The key conception of it is expressive density, it is the criterion of dense feature model and we compute out the critical value for this end. It also show that how much room to be improved for a model on a specific dataset.
## Data Related
### the file `triples.tex` re
In the directories of datasets `FB15k237`, `WN18RR` and `YAGO3-10`, there are text file named `triples` in corresponding directories. This file including the all triples from training set, validing set and testing set. This is because our model runs under the assumption of close world, the entity and relation out of knowledge graph are incapable of link predicting.
### the `.zip` file
Since the limitation of github, we have to compress the files more than 25MB into `.zip` file to upload them to the site. As a result, when run these model, you have to uncompress them.
## License

This software comes under a non-commercial use license, please see the LICENSE file.
