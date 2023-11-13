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

- *periodTimeInSeconds* : compte le nombre de secondes jouées pendant la période
- *isGoal* : indication du succès du tir
- *previousEventTypeId* : décrit l'évènement précédent
- *previousX* : la position sur l'axe X de l'évènement précédent
- *previousY* : la position sur l'axe Y de l'évènement précédent
- *distanceFromPrevious* : la distance entre le tir et l'évènement précédent
- *timeDiff* : le temps écoulé depuis l'évènement précédent
- *rebond* : indicatif tir comme évènement précédent
- *angleChange* : le changement d'angle par rapoort au filet depuis l'évènement précédent
- *vitesse* : charactérise le déplacement depuis l'évènement précédent, relativement au temps du deéplacement depuis l'évènement précédent
- *season* : saison de Hockey du match, pour s'assurer que l'acquisition des données se passe comme il se doit

Pour le Bonus nous avons rajouté : 
- *gameTime* : compte le nombre de secondes jouées pendant la partie
- *homePlayer* : indication du nombre de joueurs sur la glace de l'équipe HOME
- *awayPlayer* : indication du nombre de joueurs sur la glace de l'équipe AWAY
- *homePenaltySecondsRemaining* : le nombre de secondes de pénalité restante de l'équipe HOME
- *awayPenaltySecondsRemaining* : le nombre de secondes de pénalité restante de l'équipe AWAY
- *attackingTeamPlayer* : indication du nombre de joueur sur la glace de l'équipe attaquante
- *defendingTeamPlayer* : indication du nombre de joueur sur la glace de l'équipe défensive

## 4. Modèles avancés

Dans cette section, nous explorerons l'utilisation de modèles avancés, en particulier les classificateurs XGBoost, pour améliorer nos résultats par rapport aux modèles de régression logistique simples présentés dans la partie 3. Nous évaluerons aussi les performances en utilisant des mesures quantitatives telles que ROC/AUC, le taux de buts vs percentile de probabilité, la proportion cumulée de buts vs percentile de probabilité, et la courbe de fiabilité.

#### Entraînement du classificateur XGBoost avec les caractéristiques de distance et d'angle (Similaire à la Partie 3)

Nous avons entraîné un classificateur XGBoost en utilisant uniquement les caractéristiques de distance et d'angle, reproduisant ainsi la configuration de la partie 3. 

// glisser résultats ici avec les images et lien comet

#### Entraînement du classificateur XGBoost avec toutes les caractéristiques et réglage des hyperparamètres

Ensuite, nous avons exploré l'entraînement d'un classificateur XGBoost en utilisant toutes les caractéristiques créées dans la partie 4. Nous effectuerons des réglages d'hyperparamètres pour trouver le modèle le plus performant.

// mettre résultats et explication des choix d'hyperparamètres + lien comet

#### Exploration de la sélection de caractéristiques

Enfin, nous avons utilisé différentes techniques de sélection de caractéristiques pour simplifier notre ensemble d'entrée.

// idem res + comet



## 5. Faites de votre mieux!



## 6. Évaluer sur l'ensemble de test 