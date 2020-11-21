# Neural Network based Optimized Pruning Strategy for Statistical Machine Translation


* `Code` - This directory contains all the code written to generate the dataset and train the models
* `Dataset` - This directory contains the prepared final cleaned up dataset
* `Deployment` - This directory contains the code deployed on http://bettersmtmoses.ml/
* `Paper` - LaTeX code for the paper
* `Replicate Results` - This directory contains the code to retrain the classification models and replicate the training results

## Run Pretrained Models

  There are two scripts 

* `Code/test_model.py` (for models trained on the first feature set : XGBoost, Decision Tree, Random Forestm SGD Classifier)

* `Code/test_model_neural_and_logistic.py` (for models trained on the second feature set : Logistic Regression, Neural Network, XGBoost)

  that can be used to load up a model and a corpus file and run them all together. Pretrained models are stored in `Code/model_test/model_exports`

  Commands to run the scripts

```shell
$ python3 Code/test_model.py
$ python3 Code/test_model_neural_and_logistic.py
```

  For `Code/test_model.py`  Change the pretrained model path on line 109 for different models. The default is `model_test/model_exports/XGBoost_8Class.joblib` for the XGBoost model, replace with the following paths for the other models

* Decision Tree : `model_test/model_exports/DecisionTree_8Class.joblib`

* Random Forest : `model_test/model_exports/RandomForest_8Class.joblib`

* SGD Classifier : ``model_test/model_exports/SGDClassifier_8Class.joblib``

  For `Code/test_model_neural_and_logistic.py` Change the pretrained model path on line 43 for different models. The default is `model_test/model_exports/68acc_logistic.joblib` for the logistic regression model trained on the second feature set, replace with the following paths for the other models

- Neural Network : `model = load_model("model_test/model_exports/neural_12classes_672acc.h5")` , also uncomment line 45 to 55

- XGBoost : `model_test/model_exports/xg_boost_vectorized.joblib`

## Retrain Models

  There are 2 notebooks in the `Replicate Results` folder, 

* `All Models - First Feature Set.ipynb`

* `All Models - Second Feature Set.ipynb`

  they have the code to retrain models. Running this will reproduce the training and test accuracies for all the models described in the paper.

  To run them open the .ipynb files in Jupyter Notebook

```
$ cd Replicate\ Results
$ jupyter notebook
```

  and click on run all.

## Deployment

  Deployed at : http://bettersmtmoses.ml/

  The code for the streamlit app available in the `Deployment` folder. Follow the instructions below to run this streamlit app on a local machine.

* Install the requirements : `pip3 install -r requirements.txt`
* Run `bash setup.sh` file to perform preliminary setup
* Then run `streamlit run main.py`

  You can view the app in the browser at  `http://localhost:8501`
