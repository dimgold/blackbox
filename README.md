# BlackBox
Python open source project for parsing and reverse engineering machine learning models

![Icons made by https://www.flaticon.com/authors/freepik](https://raw.githubusercontent.com/dimgold/blackbox/master/cube-box.png)

## Project description

BlackBox project goal is to parse Machine Learning models into training data sets or directly to other model types. For example a linear model can be translated into a training dataset of features and later being retrained into a tree-based model.

This method can be used for complex models serving, models understanding, explanability and model enhancements.

## Interface

BlackBox is a python package with the following interface:

```
import blackbox as bb

dataset = bb.unbox(model,kwargs) # method to convert a model into a training dataset

lookup = bb.lookup(dataset) # trains a lookup table object

model2 = bb.rebox(model, how = clf) # retrain the model into a different model

bb.evaluate(model,model2, holdout_data = df) # evaluate models' similarity on a holdout dataset
```

## Project Scope


- ``bb.unbox()``:

  - ``method``:
    - ``bb.unbox(model, method='whitebox')``: parse model when model internals are exposed (for example ``scikit-learn`` object) 
    - ``bb.unbox(model, method='greybox')``: parse model when model internals aren't exposed but it is available for interactive queries (adverserial learning)
    - ``bb.unbox(model, method = 'blackbox')``: parse model when model internals aren't exposed and it is not available for interactive queries (one-shot learning)
    
   - ``modeltype``:
     - ``bb.unbox(model, modeltype='linear')``: parse Linear models (Linear-Regression, Logistic-Regression)
     - ``bb.unbox(model, modeltype='tree')``: parse Tree based models
     - ``bb.unbox(model, modeltype='ensemble')``: parse Ensemble Models
     - ``bb.unbox(model, modeltype='knn')``: parse KNN models
     - ``bb.unbox(model, modeltype='kmeans')``: parse K-Means models
     - ``bb.unbox(model, modeltype='svm')``: parse  SVM based models
     - ``bb.unbox(model, modeltype='dnn')``: parse Deep Neural Network models
     - ``bb.unbox(model, modeltype='cnn')``: parse CNN models
     - ``bb.unbox(model, modeltype='rnn')``: parse RNN models
     - ``bb.unbox(model, modeltype='unknown')``: parse unknown type models
     
   - ``scope``:
     - ``bb.unbox(model, scope='minimal')``: create the minimal viable dataset
     - ``bb.unbox(model, scope='maximal')``: create brute-force exhaustive dataset
     - ``bb.unbox(model, scope='defined', samples = N)``: create a dataset of N record
     - ``bb.unbox(model, scope='bootstrap')``: create a bootstrapped dataset
     - ``bb.unbox(model, scope='timebounded', time = T)``: create a bootstrapped dataset
     
     
- ``bb.rebox()``:

   - ``clf``:
     - ``bb.rebox(model, clf = clf)``: retrain into a different ``scikit-learn`` model type
     - ``bb.rebox(model, clf = 'lookup', kind = 'exact')``: retrain into a lookup table object
     - ``bb.rebox(model, clf = 'lookup' kind = 'btree')``: retrain into ``btree`` lookup object
     
     
- ``bb.lookup()``:

   - ``kind``:
     - ``bb.lookup(dataset, kind = 'exact')``: train a lookup table object
     - ``bb.lookup(dataset, , kind = 'btree')``: train a ``btree`` lookup object
   
      
- ``bb.evaluate()``:

   - ``method``:
     - ``bb.evaluate(model1, model2 , holdout_data = df, methon = 'dataset', metric = rmse, y_label = 'label')``: evaluate on holdout dataset
     - ``bb.evaluate(model1, model2 , method = 'generated', metric = rmse)``: evaluate on generated data
       
    
   

# Versions
## V0.1
Alpha version scope is to release basic functionalities as a MVP:

- ``bb.unbox(model, modeltype='linear', method = 'whitebox', scope = ['minimal'])``
- ``bb.unbox(model, modeltype='linear', method = 'whitebox', scope = ['maximal'])``

- ``bb.unbox(model, modeltype='tree', method = 'whitebox', scope = ['minimal'])``
- ``bb.unbox(model, modeltype='tree', method = 'whitebox', scope = ['maximal'])``

- ``bb.unbox(model, modeltype='knn', method = 'whitebox', scope = ['minimal'])``
- ``bb.unbox(model, modeltype='knn', method = 'whitebox', scope = ['maximal'])``

- ``bb.rebox(model, clf = clf)
- ``bb.rebox(model, clf = 'lookup', kind = 'exact')

- ``bb.lookup(dataset, kind = 'exact')

- ``bb.evaluate(model1, model2 , holdout_data = df, method = 'dataset', metric = rmse, y_label = 'label')




     



 
