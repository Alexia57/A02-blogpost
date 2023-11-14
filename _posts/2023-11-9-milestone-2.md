---
layout: post
title: Milestone 2
---


## 1. Ingénierie des caractéristiques I

### Histogramme des tirs regroupés par distance

{% include image.html url="../public/Hist_tirs_binned_distance.png" description = "Histogramme des tirs regroupés par distance"%}

Cet histogramme illustre clairement que la plupart des tirs au hockey sont des non-buts et sont répartis sur l'ensemble des distances, avec une tendance marquée pour les buts à être plus fréquents à proximité du but. On observe une concentration élevée de tirs à des distances plus courtes, ce qui diminue progressivement à mesure que la distance au but augmente. Les buts sont nettement moins nombreux que les non-buts, ce qui suggère que la distance est un indicateur significatif pour prédire les buts, mais elle ne doit pas être le seul critère utilisé étant donné la présence de buts à toutes les distances. L'importante disproportion entre les buts et les non-buts souligne également le problème potentiel de déséquilibre des classes dans les modèles prédictifs.

### Histogramme des tirs regroupés par angle

{% include image.html url="../public/Hist_tirs_binned_angles.png" description = "Histogramme des tirs regroupés par angle"%}

Cet histogramme montre la répartition des tirs au hockey en fonction de l'angle relatif au but. On remarque que les non-buts dominent largement sur l'ensemble des angles, mais la plupart des buts se produisent à des angles proches de zéro, ce qui correspond à l'angle frontal par rapport au but. La distribution des tirs est la plus dense autour de cet angle frontal, indique que les tirs sont plus fréquents et plus susceptibles d'être convertis en buts lorsqu'ils sont pris de face. Cet histogramme suggère que l'angle est un facteur important dans la prédiction des buts, bien qu'il y ait aussi des buts marqués à des angles variés, ce qui implique que d'autres facteurs doivent être pris en compte pour une prédiction précise des tirs réussis.

### Un histogramme 2D où un axe est la distance et l'autre est l'angle

{% include image.html url="../public/Hist_2D_dist_angles.png" description = "Un histogramme 2D distance et angle"%}

L'histogramme 2D présenté montre la distribution des tirs au hockey en fonction de deux variables : la distance au but (Distancetonet) et l'angle relatif au but (Relativeangletonet). 

La concentration de données montre une densité élevée de tirs à des distances plus courtes et des angles plus centrés. Cela indique que les joueurs sont susceptibles de tirer plus souvent et peut-être avec plus de succès lorsque la distance est faible et l'angle plus direct, ce qui est intuitivement cohérent avec une meilleure probabilité de marquer. À mesure que la distance augmente ou que l'angle s'éloigne du centre, la densité de tirs diminue, suggérant une baisse de la fréquence des tirs et potentiellement une moindre probabilité de conversion en but.

Cette visualisation met en évidence l'importance de la proximité et de l'orientation par rapport au but dans la probabilité de marquer, et suggère que ces deux facteurs pourraient être des prédicteurs utiles dans un modèle de régression logistique.

### Taux de buts

**Taux de buts en fonction de la distance**

{% include image.html url="../public/goal_rate_distance.png" description = "Un histogramme du taux de buts en fonction de la distance au filet"%}

Les données révèlent une corrélation significative entre la distance au filet et le taux de but. Les tirs réalisés à des distances plus courtes semblent être plus efficaces, avec un taux de but atteignant 0.2 dans la plage 0-10. Cette observation est cohérente avec l'idée générale que la proximité au filet augmente les chances de marquer. La baisse marquée du taux de but dans la plage [60-70] suggère que les joueurs peuvent rencontrer des défis particuliers à ces distances, peut-être en raison de la nécessité d'une puissance de tir accrue et d'une meilleure précision.

**Taux de buts en fonction de l'angle'**

{% include image.html url="../public/goal_rate_angle.png" description = "Un histogramme du taux de buts en fonction de l'angle relatif au filet'"%}

L'analyse des taux de but en fonction de l'angle du tir révèle des tendances intéressantes. Les angles faibles (0-120 degrés) montrent des taux de but relativement bas, indiquant la difficulté d'atteindre la cible depuis ces positions. Cependant, les angles de tir dans la plage 140-150 degrés se démarquent avec les taux de but les plus élevés, atteignant jusqu'à 0.5. Cela pourrait être dû à des facteurs tels que des ouvertures dans la défense ou une plus grande difficulté pour le gardien à intercepter ces tirs.

Globalement, les données analysées suggèrent que la proximité au filet semble jouer un rôle crucial dans le succès des tirs, avec des taux de but plus élevés observés à des distances plus courtes. De même, différentes zones d'angles de tir présentent des variations significatives dans les taux de réussite, soulignant l'importance de la précision et de la stratégie dans la sélection des angles de tir.


### Histogramme des buts classés par distance

{% include image.html url="../public/hist_goal_by_distance.png" description = "Un histogramme du nombre de buts classés par distances et en fonction du vilet (vide ou pas vide)'"%}

Les buts marqués avec le filet non vide présentent des tendances distinctes en fonction de la distance par rapport au filet. À une distance de 0-5 pieds, le nombre de buts est relativement bas, suggérant une difficulté à marquer de près, peut-être en raison de la présence immédiate du gardien de but. Cependant, une augmentation significative se produit à une distance 5-15 pieds, atteignant un pic remarquable de 6000 buts à une distance 10-15 pieds. Cette augmentation pourrait indiquer une zone de tir privilégiée, où les joueurs ont plus de chances de réussir.

Au-delà d'une distance de 78 pieds, le nombre de buts devient nul, soulignant une diminution abrupte de l'efficacité des tirs à des distances plus éloignées. Cette observation suggère que les tirs de longue distance ont peu de succès, probablement en raison d'une précision réduite ou de la facilité accrue pour le gardien de bloquer les tirs à grande distance.

En ce qui concerne les buts avec filets vides, ils se distinguent par un nombre considérablement inférieur par rapport aux buts avec filets occupés. Entre 5 et 60 pieds, la moyenne de buts est d'environ 90, indiquant que les joueurs ont plus de difficulté à marquer lorsque le gardien n’est pas présent a cet intervalle de distance. Au-delà de 50 pieds, le nombre de buts diminue progressivement, oscillant entre 70 et 50 buts, ce qui suggère une réduction de l'efficacité des tirs à des distances moyennes.

Une diminution significative se produit au-delà de 95 pieds, avec un nombre de buts chutant à environ 20. Cela souligne la rareté des buts à des distances très éloignées, indiquant une difficulté accrue pour les joueurs à marquer dans ces conditions.

En conclusion, cette analyse met en évidence l'influence significative de la distance sur l'efficacité des tirs, observant que le nombre de buts devient nul au-delà de 78 pieds lorsque le filet est non vide.Ces tendances offrent des insights précieux pour comprendre les zones de succès et d'échec des tirs.

## 2. Modèles de base

### 3.3 Analyse des résultats
La regression logistique en utilisant uniquement la distance comme caractéristique a une prédiction de 0.91 ce qui semble être une bonne performance. Mais les résultats de la matrice de confusion montrent que le modèle a enregistré 55 432 vrais négatifs et 5 728 faux négatifs. Il n'y a eu aucun vrai positif ni faux positif, ce qui signifie que le modèle a systématiquement prédit des non-buts, quelle que soit la situation.

Il existe un déséquilibre notable dans le jeu de données, avec une proportion beaucoup plus élevée de non-buts que de buts. Ce déséquilibre peut conduire le modèle à pencher vers la prédiction la plus courante, c'est-à-dire le non-but. 


Se baser uniquement sur la distance du tir pour prédire le résultat est trop simpliste. Bien que la distance puisse être un facteur influent, elle ne suffit pas à capturer toute la complexité et les nuances associées à la probabilité d'un but.

### 3.6 Interprétation des résultats 

{% include image.html url="../public/Courbe_ROC_reg_logist.png" description = "Courbe ROC et AUC"%}

{% include image.html url="../public/taux_but_centile_reg_logist.png" description = "Taux de buts par rapport au centile de probabilité"%}

{% include image.html url="../public/Prop_cumul_but_vs_percentile_prob_reg_logist.png" description = "Proportion cumulée de but vs percentile de probabilité"%}

{% include image.html url="../public/courbes_calibration_reg_logist.png" description = "Courbes de calibration"%}

#### Comet
- [Regression logistique - Distance](https://www.comet.com/ift6758-a02/milestone2/31472011c3f74857aad637eaa83e108a)
- [Regression logistique - Angle](https://www.comet.com/ift6758-a02/milestone2/3800a977222842959305eb025a4750f9)
- [Regression logistique - Distance et angle](https://www.comet.com/ift6758-a02/milestone2/2d7acf043cd54f96a27aeac1cfd059e0)

#### Courbe ROC et AUC :
Les modèles utilisant à la fois la distance et l'angle (clf_distance_angle) et uniquement la distance (clf_distance) ont une AUC de 0.70, ce qui est bien supérieur à celle du modèle utilisant uniquement l'angle (clf_angle) avec une AUC de 0.51, très proche de celle du modèle aléatoire.
Cela indique que la distance est un meilleur prédicteur des buts que l'angle, et que l'ajout de l'angle comme caractéristique ne semble pas améliorer significativement la performance du modèle par rapport à l'utilisation de la distance seule.

#### Taux de buts par rapport au centile de probabilité :
Les trois courbes sont relativement plates et proches les unes des autres ce qui indique que les modèles ont de la difficulté à différencier entre les tirs qui seront des buts et ceux qui ne le seront pas. Aucun modèle ne se démarque, ce qui pourrait signifier que ni la distance seule, ni l'angle seul, ni leur combinaison ne sont suffisants pour prédire avec précision les buts.

#### Proportion cumulée de buts vs percentile de probabilité :
Les courbes de proportion cumulée pour la distance et pour la combinaison distance-angle suivent une trajectoire similaire et se superposent presque, tandis que le modèle basé uniquement sur l'angle est sensiblement inférieur, ce qui confirme que l'angle, en tant que prédicteur unique, est moins performant.

#### Courbe de calibration :
Les modèles basés sur la distance et la combinaison distance-angle sont nettement mieux calibrés que le modèle basé sur l'angle, qui sous-estime fortement la probabilité d'événements positifs. Le modèle aléatoire, comme prévu, n'est pas calibré du tout.

En conclusion, l'ajout de l'angle ne dégrade pas les performances du modèle mais il ne les améliore pas non plus de manière notable.



## 3. Ingénierie des caractéristiques II

Voici la liste des charactéristiques créées pour cette section:

- *periodTimeInSeconds* : compte le nombre de seconde joué pendant la période, pour tenir compte d'un jeu éclair depuis le début de la période
- *isGoal* : indication du succès du tir
- *previousEventTypeId* : décrit l'évènement précédent, pour tenir compte de difficulté supplémentaire pour le guardien
- *previousX* : la position sur l'axe X de l'évènement précédent
- *previousY* : la position sur l'axe Y de l'évènement précédent
- *distanceFromPrevious* : la distance entre le tir et l'évènement précédent, pour calculer la vitesse
- *timeDiff* : le temps écoulé depuis l'évènement précédent, pour calculer la vitesse
- *rebond* : indicatif tir comme évènement précédent, pour tenir compte de difficulté supplémentaire pour le guardien
- *angleChange* : le changement d'angle par rapoort au filet depuis l'évènement précédent, pour tenir compte de difficulté supplémentaire pour le guardien
- *vitesse* : charactérise le déplacement depuis l'évènement précédent, relativement au temps du deéplacement depuis l'évènement précédent, pour tenir compte de difficulté supplémentaire pour le guardien
- *season* : saison de Hockey du match, pour s'assurer que l'acquisition des données se passe comme il se doit

Pour le Bonus nous avons rajouté : 
- *gameTime* : compte le nombre de secondes jouées pendant la partie, pour tenir compte d'un épuisement des joueurs
- *homePlayer* : indication du nombre de joueurs sur la glace de l'équipe HOME, tel que demandé
- *awayPlayer* : indication du nombre de joueurs sur la glace de l'équipe AWAY, tel que demandé
- *homePenaltySecondsRemaining* : le nombre de secondes de pénalité restante de l'équipe HOME, tel que demandé
- *awayPenaltySecondsRemaining* : le nombre de secondes de pénalité restante de l'équipe AWAY, tel que demandé
- *attackingTeamPlayer* : indication du nombre de joueur sur la glace de l'équipe attaquante, pour combiner le nombre de joueur sur la glace avec l'équipe attaquante et donc simplifié le 'vector space'
- *defendingTeamPlayer* : indication du nombre de joueur sur la glace de l'équipe défensive, pour combiner le nombre de joueur sur la glace avec l'équipe défensive et donc simplifié le 'vector space'


## 4. Modèles avancés

Dans cette section, nous explorerons l'utilisation de modèles avancés, en particulier les classificateurs XGBoost, pour améliorer nos résultats par rapport aux modèles de régression logistique simples présentés dans la partie 3. Nous évaluerons aussi les performances en utilisant des mesures quantitatives telles que ROC/AUC, le taux de buts vs percentile de probabilité, la proportion cumulée de buts vs percentile de probabilité, et la courbe de fiabilité.

### Entraînement du classificateur XGBoost avec les caractéristiques de distance et d'angle (Similaire à la Partie 3)

Dans cette étape de notre exploration, nous avons décidé d'entraîner un classificateur XGBoost en utilisant uniquement les caractéristiques de distance et d'angle, similaires à ce que nous avons fait dans la partie précédente (Partie 3). À ce stade, notre objectif n'est pas d'optimiser les hyperparamètres, mais plutôt de créer une ligne de base pour évaluer l'impact des caractéristiques supplémentaires que nous ajouterons par la suite.

#### Préparation des données
Nous avons extrait les caractéristiques pertinentes du jeu de données, se limitant à la distance par rapport au filet et à l'angle relatif par rapport au filet. 

#### Entraînement du modèle XGBoost
Nous avons utilisé le modèle XGBoost pour entraîner notre classificateur. 

#### Évaluation des performances
Une fois le modèle entraîné, nous avons évalué ses performances sur l'ensemble de validation. La matrice de confusion et diverses métriques ont été utilisées pour analyser les résultats.
Les résultats montrent une accuracy globale de 90.64%, avec des accuracies significativement différentes entre les classes 0 et 1.

#### Analyse des résultats
Pour une analyse plus approfondie, nous avons généré plusieurs graphiques, notamment la courbe ROC, le taux de buts par centile, le taux de buts cumulatif, et la courbe de calibration. Ces visualisations fournissent des insights précieux sur les performances du modèle dans différentes situations. Ici, l'aire sous la courbe (AUC) est de 0.71, le taux de but diminue en fonction du centile de probabilité et le dernier point de la courbe de calibration s'éloigne fortement de l'optimal.

{% include image.html url="../public/roc_xgb_dist_angle.png" description = "Courbe ROC et AUC modèle XGBoost avec distance et angle"%}

{% include image.html url="../public/goal_rate_xgb_dist_angle.png" description = "Taux de buts par rapport au centile de probabilité du modèle XGBoost avec distance et angle"%}

{% include image.html url="../public/cumule_xgb_dist_angle.png" description = "Proportion cumulée de but vs percentile de probabilité du modèle XGBoost avec distance et angle"%}

{% include image.html url="../public/fiabilite_xgb_dist_angle.png" description = "Courbes de calibration du modèle XGBoost avec distance et angle"%}

Lien Comet de cette expérience :

[XGBoost - Distance et angle](https://www.comet.com/ift6758-a02/milestone2/bff2db3313e549c6a53c8f57d1871550)

Dans la prochaine partie, nous enrichirons notre modèle en ajoutant plus de caractéristiques pour voir comment cela affecte ses performances.

### Entraînement du classificateur XGBoost avec toutes les caractéristiques et réglage des hyperparamètres

Dans cette étape cruciale, nous avons étendu notre modèle en utilisant toutes les caractéristiques développées dans la Partie 4 de notre exploration. Notre objectif était d'exploiter au maximum l'information disponible pour obtenir des prédictions plus précises. De plus, nous avons entrepris une recherche minutieuse d'hyperparamètres pour optimiser les performances du modèle.

#### Préparation des données
Avant d'entraîner le modèle, nous avons effectué une vérification et un nettoyage des données. Certaines caractéristiques présentaient des valeurs manquantes et infinies, auxquelles nous avons répondu en éliminant les lignes correspondantes, privilégiant ainsi la simplicité de la suppression à des changements complexes.
Ensuite, nous avons adapté le format de certaines caractéristiques pour les rendre compatibles avec l'entraînement du modèle, par exemple, en créant des variables binaires pour des caractéristiques catégorielles (ex : type de tirs).

#### Entraînement du modèle XGBoost
Nous avons divisé nos données en ensembles d'entraînement et de validation, puis procédé à l'entraînement du modèle XGBoost comme vu au dessus. 
Les performances du modèle ont montré une accuracy globale de 90.89%, avec encore des différences notables entre les classes 0 et 1.

#### Réglage des hyperparamètres
Nous avons entrepris une recherche approfondie pour trouver la combinaison optimale des hyperparamètres afin d'avoir les meilleurs résultats possibles pour le modèle. Une recherche par grille avec validation croisée a été réalisée sur un ensemble diversifié d'hyperparamètres.

Les meilleurs hyperparamètres identifiés étaient :
- colsample_bytree: 1.0
- learning_rate: 0.1
- max_depth: 5
- min_child_weight: 2
- n_estimators: 300
- subsample: 1.0
La meilleure performance obtenue avec ces hyperparamètres était une accuracy de 90.91%. La différence est très légère.

#### Comparaison avec le Modèle de Base
Pour évaluer l'impact de ces ajustements, nous avons intégré les courbes correspondantes du meilleur modèle dans nos figures existantes et comparé les résultats avec le modèle de base de la première partie de notre exploration.

{% include image.html url="../public/roc_xgbs.png" description = "Courbe ROC et AUC modèles XGBoost"%}

{% include image.html url="../public/goal_rate_xgbs.png" description = "Taux de buts par rapport au centile de probabilité des modèles XGBoost"%}

{% include image.html url="../public/cumule_xgbs.png" description = "Proportion cumulée de but vs percentile de probabilité des modèles XGBoost"%}

{% include image.html url="../public/fiabilite_xgbs.png" description = "Courbes de calibration des modèles XGBoost"%}

On remarque que l'AUC du modèle avec toutes les caractéristiques est de 0.74 et celui avec les meilleurs hyperparamètres de 0.75, ce qui est plus élevé que le modèle avec uniquement les caractéristiques de distance et d'angle. Aussi, le taux de but est plus élevé que pour le premier modèle lorsque le centile de probabilité est élevé. Enfin, les courbes de calibration des nouveaux modèles suivent plus la courbe parfaite même si n'est pas encore exactement bien.

La comparaison a révélé une légère amélioration par rapport au modèle de base, d'où l'importance de l'ajout de nouvelles caractéristiques et de chercher les meilleurs hyperparamètres.


Liens Comet vers ces expériences : 

- [XGBoost - Toutes les caractéristiques](https://www.comet.com/ift6758-a02/milestone2/b634c7efe1fc42369613d05656e8fe08)
- [XGBoost - Choix hyperparamètres](https://www.comet.com/ift6758-a02/milestone2/001b23a315ae4be486c9aac9be25c971)

Dans la prochaine partie, nous explorerons d'autres moyens d'affiner encore davantage notre modèle.

### Exploration de la sélection de caractéristiques

Enfin, nous avons entrepris d'explorer différentes techniques de sélection de caractéristiques pour simplifier notre ensemble d'entrée et potentiellement améliorer les performances du modèle XGBoost. Nous avons suivi plusieurs pistes avec des méthodes embarquées, d'encapsulation ou de filtrage. Nous avons examiné la corrélation entre les caractéristiques, utilisé la régression Lasso, la sélection récursive de caractéristiques (RFE), et exploité l'importance des caractéristiques du modèle XGBoost via SHAP.

#### Analyse de corrélation
Pour identifier des caractéristiques potentiellement redondantes, nous avons créé une matrice de corrélation. Des informations corrélées peuvent suggérer des opportunités de simplification. Les seuls carcatéristiques qui semblent bien corrélées sont "previousEventTypeId_SHOT" et "rebond" ce qui n'est pas étonnant. Puis il y a aussi "relativeAngleToNet" et "y" qui semble être un peu corrélées, mais aussi "previousEventTypeId_SHOT" et "angleChange" et enfin ce qui n'est pas surprenant vu ce qu'on vient de voir "angleChange" et "rebond". On peut donc s'attendre à voir disparaître certaines de ces caractéristiques dans la prochaine étape de sélection afin d'éviter les variables redondantes.

#### Régression Lasso
La régression Lasso a été utilisée pour pénaliser les coefficients non essentiels. On obtient ici un coefficient élevé négativement pour "distanceToNet", un un peu moins élevé positivement pour "vitesse" et encore quelques coefficients bien moins élevés dans l'ordre suivant : "timeDiff", "distanceFromPrevious", "previousY", etc. On résumé, cette méthode sélectionne les carcatéristiques suivantes : ['distanceToNet', 'vitesse', 'timeDiff', 'distanceFromPrevious', 'previousY', 'periodTimeInSeconds', 'relativeAngleToNet', 'y', 'angleChange', 'previousX'].

#### Sélection RFE
La méthode de sélection récursive de caractéristiques (RFE) a été employée pour identifier les caractéristiques les plus importantes en se basant sur l'apprentissage du modèle. Ici, les caractéristiques sélectionnées sont les mêmes que celles utilisées dans la partie 3 : ['distanceToNet', 'relativeAngleToNet'].

#### Importance des caractéristiques XGBoost
L'importance des caractéristiques a été évaluée en utilisant le modèle XGBoost lui-même. Les caractéristiques significatives ont été extraites pour simplifier l'ensemble d'entrée. A la fin, il reste encore beaucoup de caractéristiques : ['period', 'periodTimeInSeconds', 'y', 'distanceToNet', 'timeDiff', 'rebond', 'vitesse', 'typeDeTir_Backhand', 'typeDeTir_Deflected', 'typeDeTir_Slap Shot', 'typeDeTir_Snap Shot', 'typeDeTir_Tip-In', 'typeDeTir_Wrap-around', 'typeDeTir_Wrist Shot' 'previousEventTypeId_FACEOFF', 'previousEventTypeId_GIVEAWAY', 'previousEventTypeId_HIT', 'previousEventTypeId_MISSED_SHOT'].

#### SHAP
Nous avons aussi utilisé la méthode SHAP (SHapley Additive exPlanations) pour interpréter les caractéristiques sur lesquelles le modèle repose le plus. Cela nous a permi de conserver les caractéristiques : ['periodTimeInSeconds', 'y', 'distanceToNet', 'timeDiff'].

#### Évaluation des Modèles après la sélection de caractéristiques
Chaque technique de sélection de caractéristiques a été suivie d'une évaluation du modèle XGBoost avec l'ensemble réduit de caractéristiques. Les accuracies ont été calculées pour chaque approche.

#### Comparaison des performances
Les performances des différents modèles après la sélection de caractéristiques ont été comparées. Nous avons intégré les courbes correspondantes pour chaque modèle dans nos figures existantes pour une comparaison visuelle.

{% include image.html url="../public/roc_selection.png" description = "Courbe ROC et AUC modèles XGBoost méthode de sélection de caractéristiques"%}

{% include image.html url="../public/goal_rate_selection.png" description = "Taux de buts par rapport au centile de probabilité des modèles XGBoost méthode de sélection de caractéristiques"%}

{% include image.html url="../public/cumule_selection.png" description = "Proportion cumulée de but vs percentile de probabilité des modèles XGBoost méthode de sélection de caractéristiques"%}

{% include image.html url="../public/fiabilite_selection.png" description = "Courbes de calibration des modèles XGBoost méthode de sélection de caractéristiques"%}

On observe que l'AUC du modèle avec les sélections rfe est similaire à notre premier modèle XGBoost (c'est normal vu qu'il y a les mêmes caractéristiques). Sinon, la méthode qui se démarque le plus est celle qui utilise directement l'importance des caractéristiques du modèle XGBoost avec une AUC de 0.75 contre 0.72 et 0.73 pour les autres. Les mêmes conclusions se cconfirment avec les autres graphiques.

Lien Comet de cette expérience :

[XGBoost - Sélection de caractéristiques](https://www.comet.com/ift6758-a02/milestone2/f3ee208279ee48a69c4ba3eaa6196825)

## 5. Faites de votre mieux!

**Forêt aléatoire avec ACP :**
L'utilisation de l'Analyse en Composantes Principales (ACP) peut être une stratégie efficace pour améliorer la performance des modèles, en particulier dans des scénarios où le nombre de variables est élevé. Cette technique de réduction de dimensionnalité permet de simplifier les données tout en préservant leur structure d'information essentielle.
Dans notre cas, notre exploration de l'Analyse en Composantes Principales (ACP) a révélé des nuances intrigantes dans les performances de notre modèle RandomForest. Voici un aperçu succinct des résultats :

Précision Globale avec RandomForest après ACP : *90.60%*

Précision pour la Classe 0 (Non-Goal) :*99.66%*

Précision pour la Classe 1 (Goal) :*0.41%*

La classe majoritaire (Non-Goal) est prédite avec une précision élevée, conformément à la fréquence élevée de cette classe. Cependant, la prédiction des événements de but (Classe 1) montre des défis, soulignant la nécessité de peaufiner davantage notre modèle.
L'ACP a fourni des perspectives précieuses, mais des ajustements supplémentaires pourraient être explorés pour renforcer la capacité de prédiction des événements rares



**Liens vers l'entrée des expériences :**

[Forêt aléatoire avec analyse en composante principale](https://www.comet.com/ift6758-a02/milestone2/dc4807831b3545478c1982932389a018)

[Forêt aléatoire originale](https://www.comet.com/ift6758-a02/milestone2/8e40b7e7dbd649668b61935000f9d52c)

[Forêt aléatoire avec division des données](https://www.comet.com/ift6758-a02/milestone2/e6263c839798427b89d65d942f236aab)

## 6. Évaluer sur l'ensemble de test 