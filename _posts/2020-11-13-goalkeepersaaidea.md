---
layout: post
title: Idea for a project I can do in college
subtitle: Jotting down my thoughts about Goalkeeper SAA
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Art of Data]
---

## Introduction: OAA in Baseball

In baseball, one of the most predictive metrics currently in existence is OAA, or Outs Above Average. OAA attempts to measure an outfielder's defensive skill by giving outfielders credit for plays they make and punishing them for ones that they don't make based on the probability of making the play. For example, if a fly ball has a catch probability of 60%, the outfielder receives 0.4 points if he catches the ball, and loses 0.6 if he doesn't catch it. Because OAA can account for both volume and difficulty, it is considered one of the more comprehensive statistics we have. More information about OAA is available [here](https://baseballsavant.mlb.com/leaderboard/outs_above_average).

## My Idea: Goalkeeper OAA

My idea is to bring the logic behind OAA to soccer, more specifically goalkeepers. Outfielders and goalkeepers are similar in that on every play, success is a binary variable; either the play is made (catching the ball for outfielders, saving the shot for goalkeepers). Because they both have that in common, it would make sense to analyze them similarly. In order to create goalkeeper OAA (which from now on I will call SAA for saves above average), I would need to create a save probability model based on characteristics of the shot such as distance from goal, shot speed, shot height, and even curve. Once I have a save probability model, all I will have to do is pass shots and their outcomes through it to get a cumulative SAA value. However, I currently do not have either the skills or the access to data necessary to undertake this project. I plan on revisiting this idea when I am in college and possess the skills and the data to bring OAA analysis to soccer goalkeepers.

## Further details about the study:

* Identify a statistical question that I could ask.  
While creating the save probability model, I will be answering several different statistical questions at once. One of the most important ones is which characteristics of a shot are most important whether the shot results in a goal? With the project as a whole, I could answer which goalkeepers are the best at saving shots, and I could ask if my metric can predict future goalkeeper performance better then already existing metrics.
* Identify the population you would study to answer the question. What information about the population would help answer your question?  
Ideally, for the save probability model, my population would be all shots from all professional soccer leagues around the world, as the save probability model should apply to every league in every country. However, I suspect that the save probabilities will vary in leagues of different qualities, so the population I'd likely work with would be shots from the top leagues in Europe. I'd want all the player and ball tracking data that is available so I can include ball motion and location information in the model.
* Identify a feasible sample frame, and explain your reasoning.  
If I end up using the entire world as the population, there is no way I will be able to get data for every league in the world, so I'd likely pick a few top leagues. If I use just the top leagues, then I can just use all data from those leagues, and I might not have to further shrink the group I'm studying. It's important to note I'd only select shots from recent years. I wouldn't even attempt to build a model that factors in shots from 1992. I'd likely use shots from 2017-2019 to try to predict the future.
* Identify the sampling method you would use, and explain your reasoning. What makes this method better than the others?  
As previously mentioned, I wouldn't really have to shrink my dataset further if I'm only using the top leagues because obtaining data for the top leagues might actually be feasible.
* Suppose you had the means to run an experiment on this sample. Identify the null and alternative hypotheses.  
Since there's a lot of statistical questions, I'm not sure what the actual null and alternative hypothesis would be. I guess since the main goal of the project is to create a measure that is more predictive then current statistics, the null hypothesis would be "my SAA model is not more predictive then current statistics" and the alternative hypothesis would be "my SAA model is more predictive then current statistics".
*  Identify the variables and treatments that would provide information about your question. Explain your choice of treatments.  
See next question
* Identify the treatment groups, and how each subject would be assigned to a group.  
The training group would be shots from a few years, so maybe 2017-2019. The test or treatment group would be shots from a future year, like 2020.
* Briefly discuss how the experiment would be conducted.  
The experiment would take place as the soccer season goes on.
* What biases may come up, and how would you address them?  
Survivor bias will likely occur, as goalkeepers that have a low SAA, or don't perform well, will likely be cut or benched and not given another chance, meaning they will not be in the dataset for later years. The data might be filled with mostly top goalkeepers who performed well enough to survive the entire length of the experiment. I don't know how to account for this yet, but I hope to learn how to in the future.