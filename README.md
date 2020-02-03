# hyperopt_lib
a wrapper for hyperopt (hyperparamter optimization)

Usage:
```
fromr sklearn.ensemble import RandomForestRegressor
import hyperopt_lib
space = hp.choice('regressor_type', [
        {
            'type':'random_forest',
            'n_estimators': hp.choice('rf_n_trees', list(range(50, 200, 20))),
            'max_depth': hp.choice('rf_max_depth', [None] + list(range(1, 64, 2))),
            'min_samples_leaf': hp.choice('rf_min_samples_leaf', list(range(2, 32,2)))
        }
    ])
rf = RandomForestRegressor()
ho = hyperopt_lib.HyperOpt()
ho.fit(X, y, rf, space, problem_type='regression', func='kfolds', nfolds=5, max_evals=30, metric='mse')
```
