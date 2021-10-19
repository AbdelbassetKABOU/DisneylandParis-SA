

# Disneyland Paris SA

## Overview 

Le présent projet est réalisé dans le cadre de la [formation Data Engineer  de Datascientest](https://datascientest.com/formation-data-engineer).

L'objectif est de faire une analyse des reviews avec de la visualisation (distribution géographique des visiteurs, évolution des reviews dans le temps, etc), puis de l'Analyse de Sentiments _(Sentiment Analysis)_ après une étape de prétraitement. Ci-dessous, les détails et descriptions de chaque fichier.

Jeux de données  
---------------

Le dataset en question est disponible sur  : [Lien vers le dataset](https://assets-datascientest.s3-eu-west-1.amazonaws.com/de/total/reviews.csv)
Les colonnes présents dans le dataset sont les suivantes :
- **Review_Text** : contenu du commentaire,
- **Reviewer_Location** : Pays d'origine du commentaire,  
- **Year_Month** : mois du commentaire,  
- **Rating** : note sur 5 

Description des fichiers  
------------------------

- **Text_Normalization.ipynb** :   Ce notebook traite le coté prétraitement; on parlera du dataset, le processus de chargement, le filtrage (stop words), ainsi que les opérations de tokénisation, racinalisation (steeming) et Lematization. En fin, on exportera le résultat dans un fichier csv qui sera par la suite utilisé pour effectuer le reste des opérations demandées (exploration, visualisation et analyse).

- **DataViz_WordCloud.ipynb** :   Dans cette partie, nous allons procéder à une analyse exploratoire avec une partie visualisation.

- **Predictions_01.ipynb** :  Nous testons différents algo de Machine Learning : _Gradient Boosting, Logistic Regression, Multinomial NB, Random Forest_. Nous allons les évaluer et voir que, dans les meilleurs des cas, les performances ne dépasseraient pas les _82%_. Plus de techniques (notamment de vectorisation) vont être utilisées au cours du notebook suivants et qui vont impacter considérablement les performances obtenus.


- **Predictions_02.ipynb** :  L'objectif est d'améliorer les performances obtenus précédemment. Pour ce faire on testera 4 nouvelles techniques de vectorisations, i.e. _Unigram Counts, Unigram Tf-Idf, _ Bigram Counts_, Bigram Tf-Idf_. Afin de choisir la meilleur technique, pour chaque stratégie, nous divisons le dataset en data de formation/validation puis nous formons un _SGDClassifier_ et calculons le score. Nous allons par la suite ajuster le modèle obtenu, en cherchant la meilleure combinaison des paramètres (i) _loss, learning rate_ et _initial learning rate_, puis (ii) _Penalty_ et _Alpha_. Le notebook permet également de sauvegarder le _(meilleur)_ classifieur sous le répertoire _classifiers_ puis le charger à nouveau par la suite. 

Au final, nous obtenons une précision dans les alentours de _90%_ largement supérieures aux modèles précédentes et relativement convainquant par rapport à un modèle _linéaire simple_. Il existe néanmoins des méthodes plus avancées qui donnent de meilleurs résultats. L'état actuel de l'art sur des dataset de ce type est de 97,42% [1, 2].

# Références

- **[1]  :** https://towardsdatascience.com/building-a-sentiment-classifier-using-scikit-learn-54c8e7c5d2f0
- **[2]  :** https://www.aclweb.org/anthology/P19-2057.pdf

