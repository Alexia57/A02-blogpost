---
layout: post
title: Milestone 2
---


## 1. Ingénierie des caractéristiques I

blabla

## 2. Modèles de base

### 3.3 Analyse des résultats
La regression logistique avec uniquement la distance a une prédiction de 0.91 ce qui semble être une performance. Mais les résultats de la matrice de confusion montrent que le modèle a enregistré 55 432 vrais négatifs et 5 728 faux négatifs. Il n'y a eu aucun vrai positif ni faux positif, ce qui signifie que le modèle a systématiquement prédit des non-buts, quelle que soit la situation.

Il existe un déséquilibre notable dans le jeu de données, avec une proportion beaucoup plus élevée de non-buts que de buts. Ce déséquilibre peut conduire le modèle à pencher vers la prédiction la plus courante, c'est-à-dire le non-but. 


Se baser uniquement sur la distance du tir pour prédire le résultat est trop simpliste. Bien que la distance puisse être un facteur influent, elle ne suffit pas à capturer toute la complexité et les nuances associées à la probabilité d'un but.

### 3.6 Interprétation des résultats 

{% include Courbe_ROC_reg_logist.html url="../public/Courbe_ROC_reg_logist.png" description = "Courbe ROC et AUC"%}

{% include taux_but_centile_reg_logist.html url="../public/taux_but_centile_reg_logist.png" description = "Taux de buts par rapport au centile de probabilité"%}

{% include Prop_cumul_but_vs_percentile_prob_reg_logist.html url="../public/Prop_cumul_but_vs_percentile_prob_reg_logist.png" description = "Proportion cumulée de but vs percentile de probabilité"%}

{% include courbes_calibration_reg_logist.html url="../public/courbes_calibration_reg_logist.png" description = "Courbes de calibration"%}

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



## 4. Modèles avancés



## 5. Faites de votre mieux!



## 6. Évaluer sur l'ensemble de test 