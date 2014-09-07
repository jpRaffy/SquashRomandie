---
title: "Squash Romandie - Season 2013-2014"
author: "Jean-Paul Raffy"
copyright: jpRaffy
date: "1 September 2014"
keywords:
  Squash
  Romandie
  Season
  League
  2013
  2014
  Insight
output:
  html_document:
    fig_height: 4
    theme: cosmo
    toc: yes
---





### Introduction

This study has been conducted during the second half of August 2014. Its purpose is to perform some data analysis on match results for the [Squash Romandie](http://squashromandie.ch) regional league of [squash](http://en.wikipedia.org/wiki/Squash_%28sport%29). **Squash Romandie (SR)** groups together 18 sports clubs mainly focused on squash and located in [Suisse romande](http://en.wikipedia.org/wiki/Suisse_romande), the French-speaking part of Switzerland.

Every season, between the beginning of September and the end of June of next year, official matches, tournaments and interclubs are organised for licensed players of the **SR** organisation. Depending of the matches outcomes, points are awarded to the winning player and deducted from the loosing player's ranking, according of the ranking difference between the 2 players and the score.

The data collected for this study from the [SR](http://squashromandie.ch) website, represents all the results for the 2013-2014 season as of **7 August 2014**.

---


### Data

This study is based on 4 data files, collected from the website:

1. `Clubs.txt` contains the 18 [clubs](http://squashromandie.ch/club), identified by their 3 letters codes
2. `Players.txt` contains the [players](http://squashromandie.ch/player), identified by their last name, first name, license number and their club
3. `Rankings.txt` contains the [rankings](http://squashromandie.ch/ranking/overall) for all licensed players, identified by their names, license number and club
4. `Results.txt` contains the aggregated results for all the players. The following link shows the [results](http://squashromandie.ch/ranking/detail/4023) for the top-ranked player, identified by its license number 4023. Apart from the columns identifying the player that are self-explanatory, the other columns are described hereafter:

    * `Date`: the day the match was played expressed as `dd.mm.yyyy`
    * `Event`: the event when the match was played. Usually, a mini-league (intraclub match), a tournament or an interclub
    * `Result`: the match outcome in plain text in French. *Bat* reprensents a win, and *Perd contre* represents a defeat
    * `Score`: the score expresses the match outcome with the perspective of the listed player, and not his opponent. Matches are usually played to "best-of-five" (i.e. the first player to win three games)
    * `Gain`: the number of points earned in case positive, or conceded otherwise
    * `Points`: the ranking after the points under the `Gain` column have beed added or substracted from the previous ranking



<br>


Line samples of these 4 data files are given below:
<br>

First 3 clubs from the `Clubs.txt` data file:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:01 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Club </TH> <TH> Description </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> ALC </TD> <TD> Alcatraz Renens </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> ATL </TD> <TD> Gland  </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> BIE </TD> <TD> Bienne </TD> </TR>
   </TABLE>
<br>

First 3 players from the `Players.txt` data file:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:01 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Club </TH> <TH> License </TH> <TH> Last.Name </TH> <TH> First.Name </TH> <TH> Player </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> ALC </TD> <TD align="right"> 1004 </TD> <TD> Abella </TD> <TD> Pedro </TD> <TD> Abella, Pedro (ALC) </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> ALC </TD> <TD align="right"> 1005 </TD> <TD> Bourgeois </TD> <TD> François-Marie </TD> <TD> Bourgeois, François-Marie (ALC) </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> ALC </TD> <TD align="right"> 1006 </TD> <TD> Von Tobel </TD> <TD> Lukas </TD> <TD> Von Tobel, Lukas (ALC) </TD> </TR>
   </TABLE>
<br>

First 3 rankings from the `Rankings.txt` data file:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:01 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Points </TH> <TH> Club </TH> <TH> License </TH> <TH> Last.Name </TH> <TH> First.Name </TH> <TH> Player </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD align="right"> 451.28 </TD> <TD> GEN </TD> <TD align="right"> 4023 </TD> <TD> Bolay </TD> <TD> Nicolas </TD> <TD> Bolay, Nicolas (GEN) </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD align="right"> 356.29 </TD> <TD> MEY </TD> <TD align="right"> 7018 </TD> <TD> DCruz </TD> <TD> Conor </TD> <TD> DCruz, Conor (MEY) </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD align="right"> 344.91 </TD> <TD> ATL </TD> <TD align="right"> 2086 </TD> <TD> Billebault </TD> <TD> Gregory </TD> <TD> Billebault, Gregory (ATL) </TD> </TR>
   </TABLE>
<br>

First 3 results from the `Results.txt` data file:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:01 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Last.Name </TH> <TH> First.Name </TH> <TH> Ranking </TH> <TH> Club </TH> <TH> License </TH> <TH> Date </TH> <TH> Event </TH> <TH> Result </TH> <TH> Score </TH> <TH> Gain </TH> <TH> Points </TH> <TH> Player </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Bolay </TD> <TD> Nicolas </TD> <TD align="right"> 451.28 </TD> <TD> GEN </TD> <TD align="right"> 4023 </TD> <TD> 08.04.2014 </TD> <TD> Squash Romandie Interclub Hommes 2013/2014 </TD> <TD> Bat Gregory Bohren (303.73) </TD> <TD> 3-1 </TD> <TD align="right"> 1.00 </TD> <TD align="right"> 451.28 </TD> <TD> Bolay, Nicolas (GEN) </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Bolay </TD> <TD> Nicolas </TD> <TD align="right"> 451.28 </TD> <TD> GEN </TD> <TD align="right"> 4023 </TD> <TD> 25.02.2014 </TD> <TD> Squash Romandie Interclub Hommes 2013/2014 </TD> <TD> Bat Fabrice Collot (313) </TD> <TD> 3-0 </TD> <TD align="right"> 1.00 </TD> <TD align="right"> 450.28 </TD> <TD> Bolay, Nicolas (GEN) </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Bolay </TD> <TD> Nicolas </TD> <TD align="right"> 451.28 </TD> <TD> GEN </TD> <TD align="right"> 4023 </TD> <TD> 08.02.2014 </TD> <TD> Sion A </TD> <TD> Bat Olivier Sprungli (323.05) </TD> <TD> 3-1 </TD> <TD align="right"> 1.00 </TD> <TD align="right"> 449.28 </TD> <TD> Bolay, Nicolas (GEN) </TD> </TR>
   </TABLE>

---


### Clubs & Players

#### **Who's who**

As of **7 August 2014**, there were **18** clubs with a total number of **699** licensed players. For more clarity over this study, colours have been assigned to each club, as much as possible inspired by their colour identity. The clubs and respective colours are shown below:

![plot of chunk clubs](figure/clubs.png) 


#### **Who's where**

The following chart lists the clubs according to their **SR** licensed players, from most to least important:

![plot of chunk playersbyclubs](figure/playersbyclubs.png) 


#### **Who's strong**

In the following chart, the clubs are compared in terms of density of rankings. The tiny horizontal black segments in each box reprensent the median ranking for the licensed player in each club. Orange dots represent the outlying points in each density. Notice that the **UGE** club with **7** licensed players has no rankings, as it has recently opened.

![plot of chunk dentitybyrankings](figure/dentitybyrankings.png) 


The following chart lists the clubs according to the average weight of their licensed players. This helps to identify which clubs concentrate top-ranking players. It is interesting to note that here again, the **UGE** club has an average ranking of **0**.

![plot of chunk clubsbyrelweight](figure/clubsbyrelweight.png) 


#### **Who's most active**

It is important to highlight that not all licensed players actually engage in **SR** competitions. Indeed, there are **136** out of **699** players that never participated to an event over the 2013-2014 season. Excluding these "inactive" players, gives another interesting perspective to the average weight of **active** licensed players by club:

![plot of chunk clubsbyrelweightnona](figure/clubsbyrelweightnona.png) 


#### **Who's least active**

Let's find out in which clubs and how many by club, are these licensed players who never engaged in any **SR** competition over the 2013-2014 season. This is shown in the following chart:

![plot of chunk inactiveplayers](figure/inactiveplayers.png) 


#### **Who's played a lot**

On the other side of the spectrum, and amongst the **12215** recorded matches, the 10 most active players over the season are listed in the table below:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:06 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Ranking </TH> <TH> Event </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Maillardet, Samuel (PUI) </TD> <TD align="right"> 172.50 </TD> <TD align="right"> 161 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Roijer, Christophe (GRS) </TD> <TD align="right"> 85.66 </TD> <TD align="right"> 135 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Blangiforti, Laurent (PUI) </TD> <TD align="right"> 175.12 </TD> <TD align="right"> 131 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Duvanel, Julien (ALC) </TD> <TD align="right"> 239.94 </TD> <TD align="right"> 129 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> McNicol, Jonathan (ALC) </TD> <TD align="right"> 144.17 </TD> <TD align="right"> 111 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Magnin, Thierry (ALC) </TD> <TD align="right"> 198.45 </TD> <TD align="right"> 102 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Coley, Brian (ALC) </TD> <TD align="right"> 206.27 </TD> <TD align="right"> 101 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Chevalley, Pierre-André (PUI) </TD> <TD align="right"> 116.68 </TD> <TD align="right">  98 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Perrin, Xavier (ALC) </TD> <TD align="right"> 125.68 </TD> <TD align="right">  95 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Gameiro, Paulo (PUI) </TD> <TD align="right"> 171.77 </TD> <TD align="right">  93 </TD> </TR>
   </TABLE>
<br>


Subsequently, the most active clubs are summarised in the following chart:

![plot of chunk eventsbyclub](figure/eventsbyclub.png) 








#### **Who’s earned most points on average**

Let's now consider the top-10 players with the best average gained points per event. The `Total` column shows the number of earned points by a player over the season, with the number of event to which he/she has participated, under the `Count` column. 

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:20 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Start </TH> <TH> End </TH> <TH> Total </TH> <TH> Event </TH> <TH> Average </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Aziz, Nabil (CCG) </TD> <TD> 2013-11-19 </TD> <TD> 2014-04-22 </TD> <TD align="right"> 32.80 </TD> <TD align="right">   5 </TD> <TD align="right"> 6.56 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Emch, Olivier (COL) </TD> <TD> 2013-11-12 </TD> <TD> 2014-01-07 </TD> <TD align="right"> 10.06 </TD> <TD align="right">   2 </TD> <TD align="right"> 5.03 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Lanio, Jean-Marie (MAR) </TD> <TD> 2014-02-18 </TD> <TD> 2014-02-18 </TD> <TD align="right"> 4.83 </TD> <TD align="right">   1 </TD> <TD align="right"> 4.83 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Soares, Rui (COL) </TD> <TD> 2014-03-20 </TD> <TD> 2014-03-20 </TD> <TD align="right"> 13.50 </TD> <TD align="right">   3 </TD> <TD align="right"> 4.50 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Martinez, David (MEY) </TD> <TD> 2013-10-01 </TD> <TD> 2013-10-01 </TD> <TD align="right"> 4.42 </TD> <TD align="right">   1 </TD> <TD align="right"> 4.42 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Evrard, Jean-Marie (GEN) </TD> <TD> 2014-07-29 </TD> <TD> 2014-07-29 </TD> <TD align="right"> 8.51 </TD> <TD align="right">   2 </TD> <TD align="right"> 4.25 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Sudan, Frederic (GRU) </TD> <TD> 2013-11-26 </TD> <TD> 2013-11-26 </TD> <TD align="right"> 4.16 </TD> <TD align="right">   1 </TD> <TD align="right"> 4.16 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Newsome, Paul (CTG) </TD> <TD> 2013-10-15 </TD> <TD> 2014-04-09 </TD> <TD align="right"> 33.03 </TD> <TD align="right">   8 </TD> <TD align="right"> 4.13 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Sirmakes, Sisvan (CCG) </TD> <TD> 2013-10-08 </TD> <TD> 2014-04-22 </TD> <TD align="right"> 28.57 </TD> <TD align="right">   7 </TD> <TD align="right"> 4.08 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Crowley, Kevin (CCG) </TD> <TD> 2013-10-22 </TD> <TD> 2014-04-22 </TD> <TD align="right"> 11.60 </TD> <TD align="right">   3 </TD> <TD align="right"> 3.87 </TD> </TR>
   </TABLE>
<br>


Looking at the previous statistic per player, the following chart gives the best average gained points by event and by club:

![plot of chunk bestmeanbyclub](figure/bestmeanbyclub.png) 


#### **Top performers**

To rank the players by performance, the `Initial`, `Final`and `Performance` columns are added to the summarised data. The `Performance` is calculated with the `(Final - Initial) / Initial` formula, and expressed raw and not in percent. The following table lists the top-10 performers over the season, while excluding players with initial starting points below 10, in order to avoid abnormally high values, obtained when `Initial` is near 0.

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:21 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Start </TH> <TH> End </TH> <TH> Initial </TH> <TH> Final </TH> <TH> Total </TH> <TH> Performance </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Collazo, Javier (MAR) </TD> <TD> 2013-11-16 </TD> <TD> 2014-04-25 </TD> <TD align="right"> 34.03 </TD> <TD align="right"> 167.60 </TD> <TD align="right"> 133.57 </TD> <TD align="right"> 3.93 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Roberge, Charles (PUI) </TD> <TD> 2013-08-30 </TD> <TD> 2014-05-31 </TD> <TD align="right"> 22.14 </TD> <TD align="right"> 89.65 </TD> <TD align="right"> 67.51 </TD> <TD align="right"> 3.05 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Carranza, David (PUI) </TD> <TD> 2013-08-30 </TD> <TD> 2014-07-03 </TD> <TD align="right"> 14.18 </TD> <TD align="right"> 50.73 </TD> <TD align="right"> 36.55 </TD> <TD align="right"> 2.58 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Tornay, Flavien (PUI) </TD> <TD> 2013-09-30 </TD> <TD> 2014-07-03 </TD> <TD align="right"> 13.35 </TD> <TD align="right"> 47.66 </TD> <TD align="right"> 34.31 </TD> <TD align="right"> 2.57 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Riedi, Loic (ALC) </TD> <TD> 2013-08-31 </TD> <TD> 2014-06-30 </TD> <TD align="right"> 28.05 </TD> <TD align="right"> 99.47 </TD> <TD align="right"> 71.42 </TD> <TD align="right"> 2.55 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Staehli, Raphael (GRS) </TD> <TD> 2013-09-06 </TD> <TD> 2014-04-11 </TD> <TD align="right"> 15.63 </TD> <TD align="right"> 47.82 </TD> <TD align="right"> 32.19 </TD> <TD align="right"> 2.06 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Joss, Ludovic (ALC) </TD> <TD> 2013-11-09 </TD> <TD> 2014-02-13 </TD> <TD align="right"> 10.85 </TD> <TD align="right"> 32.85 </TD> <TD align="right"> 22.00 </TD> <TD align="right"> 2.03 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Duvanel, Julien (ALC) </TD> <TD> 2013-08-31 </TD> <TD> 2014-06-30 </TD> <TD align="right"> 82.74 </TD> <TD align="right"> 239.94 </TD> <TD align="right"> 157.20 </TD> <TD align="right"> 1.90 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Tougarinoff, Iouri (PUI) </TD> <TD> 2013-08-30 </TD> <TD> 2014-05-31 </TD> <TD align="right"> 38.06 </TD> <TD align="right"> 104.65 </TD> <TD align="right"> 66.59 </TD> <TD align="right"> 1.75 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Kingsada, Vira (PUI) </TD> <TD> 2013-08-30 </TD> <TD> 2014-05-31 </TD> <TD align="right"> 11.67 </TD> <TD align="right"> 31.54 </TD> <TD align="right"> 19.87 </TD> <TD align="right"> 1.70 </TD> </TR>
   </TABLE>
<br>


To rank the clubs by performance, the same principle applied above is performed at the clubs' summarised data. Again, the `Performance` is expressed in raw terms and not in percent.

![plot of chunk bestperfbyclub](figure/bestperfbyclub.png) 


#### **Unbeatables...**

Let's find out now all the players who never lost a match over the season. The following table lists the number of wins under the `Win` column and the number of elapsed days between the first and last event's dates under the `Days` column. The column `Frequency` is calculated according to the `(Win / Days) * 100` formula, indicating many wins over a short period of time, when the value is high. The wins and frequencies are then displayed in a chart, below the table:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:21 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Days </TH> <TH> Event </TH> <TH> Win </TH> <TH> Loss </TH> <TH> Frequency </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Bolay, Nicolas (GEN) </TD> <TD align="right"> 215 </TD> <TD align="right">  36 </TD> <TD align="right">  36 </TD> <TD align="right">   0 </TD> <TD align="right"> 16.74 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Valentin, Angel (ALC) </TD> <TD align="right"> 155 </TD> <TD align="right">  12 </TD> <TD align="right">  12 </TD> <TD align="right">   0 </TD> <TD align="right"> 7.74 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Etienne, Fabrice (COL) </TD> <TD align="right"> 218 </TD> <TD align="right">  11 </TD> <TD align="right">  11 </TD> <TD align="right">   0 </TD> <TD align="right"> 5.05 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Ganeau, Hervé (ATL) </TD> <TD align="right">  47 </TD> <TD align="right">  11 </TD> <TD align="right">  11 </TD> <TD align="right">   0 </TD> <TD align="right"> 23.40 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Jeker, Pascal (ALC) </TD> <TD align="right"> 213 </TD> <TD align="right">  11 </TD> <TD align="right">  11 </TD> <TD align="right">   0 </TD> <TD align="right"> 5.16 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Cowhie, Michael (BIE) </TD> <TD align="right"> 216 </TD> <TD align="right">   7 </TD> <TD align="right">   7 </TD> <TD align="right">   0 </TD> <TD align="right"> 3.24 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Marques, Edouardo (COL) </TD> <TD align="right"> 106 </TD> <TD align="right">   5 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right"> 4.72 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Pilloux, Hervé (MEY) </TD> <TD align="right"> 155 </TD> <TD align="right">   4 </TD> <TD align="right">   4 </TD> <TD align="right">   0 </TD> <TD align="right"> 2.58 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Martignoni, Jacques (SIO) </TD> <TD align="right">  57 </TD> <TD align="right">   3 </TD> <TD align="right">   3 </TD> <TD align="right">   0 </TD> <TD align="right"> 5.26 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Emch, Olivier (COL) </TD> <TD align="right">  57 </TD> <TD align="right">   2 </TD> <TD align="right">   2 </TD> <TD align="right">   0 </TD> <TD align="right"> 3.51 </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD> Godot, Philippe (ALC) </TD> <TD align="right">  32 </TD> <TD align="right">   2 </TD> <TD align="right">   2 </TD> <TD align="right">   0 </TD> <TD align="right"> 6.25 </TD> </TR>
   </TABLE>
![plot of chunk onlywinners](figure/onlywinners.png) 


#### **... and beatables**

Symmetrically, the following table and chart list all the players who never won a match over the season. The following table lists the number of losses under the `Loss` column. The column `Frequency` is calculated according to the `(Loss / Days) * 100` formula, indicating many losses over a short period of time, when the value is high. The losses and frequencies are then displayed in a chart, below the table:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:47:22 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Days </TH> <TH> Event </TH> <TH> Win </TH> <TH> Loss </TH> <TH> Frequency </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Barelli, Philibert (ALC) </TD> <TD align="right"> 151 </TD> <TD align="right">  17 </TD> <TD align="right">   0 </TD> <TD align="right">  17 </TD> <TD align="right"> 11.26 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Nicolet, Philippe (YVE) </TD> <TD align="right"> 213 </TD> <TD align="right">  17 </TD> <TD align="right">   0 </TD> <TD align="right">  17 </TD> <TD align="right"> 7.98 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Fontaine, Luc (ALC) </TD> <TD align="right">  65 </TD> <TD align="right">  14 </TD> <TD align="right">   0 </TD> <TD align="right">  14 </TD> <TD align="right"> 21.54 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Bolay, Cecilia (GEN) </TD> <TD align="right"> 197 </TD> <TD align="right">  10 </TD> <TD align="right">   0 </TD> <TD align="right">  10 </TD> <TD align="right"> 5.08 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Bussien, Christian (BIE) </TD> <TD align="right"> 256 </TD> <TD align="right">   9 </TD> <TD align="right">   0 </TD> <TD align="right">   9 </TD> <TD align="right"> 3.52 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Christinaz, Jérémie (BIE) </TD> <TD align="right">  36 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> 16.67 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Franco, Michel (GEN) </TD> <TD align="right">  22 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> 27.27 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Labeydh, Aziz (CTG) </TD> <TD align="right"> 155 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> 3.87 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Siquier, Audrey (PUI) </TD> <TD align="right">  31 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> 19.35 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Walzer, Fabienne (GRS) </TD> <TD align="right">  99 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> 6.06 </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD> Jorand, Anouk (SIO) </TD> <TD align="right">  46 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right">   5 </TD> <TD align="right"> 10.87 </TD> </TR>
  <TR> <TD align="right"> 12 </TD> <TD> Juillard, Richard (SIO) </TD> <TD align="right"> 141 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right">   5 </TD> <TD align="right"> 3.55 </TD> </TR>
  <TR> <TD align="right"> 13 </TD> <TD> Puig, Nuria (GRS) </TD> <TD align="right">  31 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right">   5 </TD> <TD align="right"> 16.13 </TD> </TR>
  <TR> <TD align="right"> 14 </TD> <TD> Laederach, Tania (ALC) </TD> <TD align="right">  38 </TD> <TD align="right">   3 </TD> <TD align="right">   0 </TD> <TD align="right">   3 </TD> <TD align="right"> 7.89 </TD> </TR>
  <TR> <TD align="right"> 15 </TD> <TD> Mascheroni, Sarah (GEN) </TD> <TD align="right"> 155 </TD> <TD align="right">   3 </TD> <TD align="right">   0 </TD> <TD align="right">   3 </TD> <TD align="right"> 1.94 </TD> </TR>
  <TR> <TD align="right"> 16 </TD> <TD> Thura, Zaw (ALC) </TD> <TD align="right">  62 </TD> <TD align="right">   3 </TD> <TD align="right">   0 </TD> <TD align="right">   3 </TD> <TD align="right"> 4.84 </TD> </TR>
  <TR> <TD align="right"> 17 </TD> <TD> Clerc, Serge (SIO) </TD> <TD align="right">  43 </TD> <TD align="right">   2 </TD> <TD align="right">   0 </TD> <TD align="right">   2 </TD> <TD align="right"> 4.65 </TD> </TR>
   </TABLE>
![plot of chunk onlyloosers](figure/onlyloosers.png) 


#### **Winners & loosers**

The top-5 winners and top-5 loosers in terms of earned points are shown in the following chart:

![plot of chunk winnersandloosers](figure/winnersandloosers.png) 


#### **And the winner is...**

The following chart displays the ranking's evolution over the season for the top winner. The horizontal and vertical dotted lines indicate when the maximum ranking was reached. The statistics above the chart are described as follows:

* `P`: number of event **P**layed
* `W`: number of **W**ins
* `L`: number of **L**osses
* `Pn`: number of points lost due to **P**e**n**alities
* `Pt`: number of **P**oin**t**s earned
* `M`: **M**aximum ranking reached over the season
* `m`: **m**inimum ranking reached over the season

![plot of chunk winnervariationchart](figure/winnervariationchart.png) 


#### **Who to bet your money on?**

The following table gathers the top-20 confrontations by couple of players, with the total of matches listed under the `Count` column, the number of wins under the `Win` column and the number of losses under the `Loss` column:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:48:06 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> FromPlayer </TH> <TH> ToPlayer </TH> <TH> Count </TH> <TH> Win </TH> <TH> Loss </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Blangiforti, Laurent (PUI) </TD> <TD> Maillardet, Samuel (PUI) </TD> <TD align="right">  16 </TD> <TD align="right">   8 </TD> <TD align="right">   8 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Coley, Brian (ALC) </TD> <TD> Duvanel, Julien (ALC) </TD> <TD align="right">  14 </TD> <TD align="right">   5 </TD> <TD align="right">   9 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Duvanel, Julien (ALC) </TD> <TD> Magnin, Thierry (ALC) </TD> <TD align="right">  13 </TD> <TD align="right">  10 </TD> <TD align="right">   3 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Blangiforti, Laurent (PUI) </TD> <TD> Gameiro, Paulo (PUI) </TD> <TD align="right">  10 </TD> <TD align="right">   2 </TD> <TD align="right">   8 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Coley, Brian (ALC) </TD> <TD> Magnin, Thierry (ALC) </TD> <TD align="right">  10 </TD> <TD align="right">   4 </TD> <TD align="right">   6 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Bruand, Martin (YVE) </TD> <TD> Girardet, Julien (YVE) </TD> <TD align="right">   9 </TD> <TD align="right">   5 </TD> <TD align="right">   4 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Chevalley, Pierre-André (PUI) </TD> <TD> Maillardet, Samuel (PUI) </TD> <TD align="right">   9 </TD> <TD align="right">   1 </TD> <TD align="right">   8 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Chevalley, Pierre-André (PUI) </TD> <TD> Gameiro, Paulo (PUI) </TD> <TD align="right">   8 </TD> <TD align="right">   1 </TD> <TD align="right">   7 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Fidalgo, Antonio (GRS) </TD> <TD> Zigliani, Julien (GRS) </TD> <TD align="right">   8 </TD> <TD align="right">   5 </TD> <TD align="right">   3 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Grogg, Julien (PUI) </TD> <TD> Marthaler, Joel (PUI) </TD> <TD align="right">   8 </TD> <TD align="right">   0 </TD> <TD align="right">   8 </TD> </TR>
  <TR> <TD align="right"> 11 </TD> <TD> Maillardet, Samuel (PUI) </TD> <TD> Morris, Rupert (PUI) </TD> <TD align="right">   8 </TD> <TD align="right">   4 </TD> <TD align="right">   4 </TD> </TR>
  <TR> <TD align="right"> 12 </TD> <TD> Blangiforti, Laurent (PUI) </TD> <TD> McNicol, Jonathan (ALC) </TD> <TD align="right">   7 </TD> <TD align="right">   5 </TD> <TD align="right">   2 </TD> </TR>
  <TR> <TD align="right"> 13 </TD> <TD> Blangiforti, Laurent (PUI) </TD> <TD> Morris, Rupert (PUI) </TD> <TD align="right">   7 </TD> <TD align="right">   2 </TD> <TD align="right">   5 </TD> </TR>
  <TR> <TD align="right"> 14 </TD> <TD> De Jonge, Marie-José (PUI) </TD> <TD> Isely, Stéphane (PUI) </TD> <TD align="right">   7 </TD> <TD align="right">   0 </TD> <TD align="right">   7 </TD> </TR>
  <TR> <TD align="right"> 15 </TD> <TD> De Jonge, Marie-José (PUI) </TD> <TD> Wagner, David (PUI) </TD> <TD align="right">   7 </TD> <TD align="right">   5 </TD> <TD align="right">   2 </TD> </TR>
  <TR> <TD align="right"> 16 </TD> <TD> Favre, David (GRS) </TD> <TD> Inan, Enaitz (GRS) </TD> <TD align="right">   7 </TD> <TD align="right">   4 </TD> <TD align="right">   3 </TD> </TR>
  <TR> <TD align="right"> 17 </TD> <TD> Ferrot, Patrice (YVE) </TD> <TD> Steppacher, Noe (YVE) </TD> <TD align="right">   7 </TD> <TD align="right">   1 </TD> <TD align="right">   6 </TD> </TR>
  <TR> <TD align="right"> 18 </TD> <TD> Gameiro, Paulo (PUI) </TD> <TD> Maillardet, Samuel (PUI) </TD> <TD align="right">   7 </TD> <TD align="right">   5 </TD> <TD align="right">   2 </TD> </TR>
  <TR> <TD align="right"> 19 </TD> <TD> Lopez, Andres (GRS) </TD> <TD> Zigliani, Julien (GRS) </TD> <TD align="right">   7 </TD> <TD align="right">   7 </TD> <TD align="right">   0 </TD> </TR>
  <TR> <TD align="right"> 20 </TD> <TD> Ackermann, Valentin (BIE) </TD> <TD> Christinaz, Alain (BIE) </TD> <TD align="right">   6 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> </TR>
   </TABLE>
<br>


#### **No-shows**

Players that do not show at events they are registered to, are penalised and loose 6 points. The table below shows the penalties over the season:

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:48:06 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Start </TH> <TH> End </TH> <TH> Days </TH> <TH> Event </TH> <TH> Penalty </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Garzon, Juan-Pablo (GEN) </TD> <TD> 2013-08-27 </TD> <TD> 2014-07-29 </TD> <TD align="right"> 337 </TD> <TD align="right">  55 </TD> <TD align="right">   1 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Charpilloz, Nicolas (BIE) </TD> <TD> 2013-09-06 </TD> <TD> 2014-05-24 </TD> <TD align="right"> 261 </TD> <TD align="right">  54 </TD> <TD align="right">   1 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Cucuzza, Michael (GRU) </TD> <TD> 2013-09-06 </TD> <TD> 2014-07-03 </TD> <TD align="right"> 301 </TD> <TD align="right">  43 </TD> <TD align="right">   1 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Krajcinovic, Uros (COL) </TD> <TD> 2013-11-08 </TD> <TD> 2014-05-24 </TD> <TD align="right"> 198 </TD> <TD align="right">  29 </TD> <TD align="right">   1 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Billebault, Gregory (ATL) </TD> <TD> 2013-10-08 </TD> <TD> 2014-01-29 </TD> <TD align="right"> 114 </TD> <TD align="right">   6 </TD> <TD align="right">   1 </TD> </TR>
   </TABLE>

---


### Interclubs

Each season, [interclub](http://squashromandie.ch/interclub) matches are organised by leagues. For the 2013-2014 season, there were 6 different leagues with approximately 7 teams by league, entered by their respective clubs:

* Super Ligue
* Ligue 1
* Ligue 2 Ouest
* Ligue 2 Est
* Ligue 3 Ouest
* Ligue 3 Est

Each team is composed of 4 players, and may be mixed (male & female). Encounters are organised to be played at home and away, each player of receiving team playing another player of the visiting team, according to rankings. The 4 matches results are aggregated resulting in the following outcomes:

* G: Win *(Gagné)*
* E+ : Winning draw (games) *(Gagné (sets))*
* E : Draw *(Egalité)*
* P : Loss *(Perdu)*

Players of the same club may be part of more than 1 team, thus resulting in more interclub results at an individual level. Also, matches played during the Interclub season, contribute to the players' individual rankings.






<br>


#### **Players you want in your teams...**

The following table show the top-10 best performers in interclubs encounters. The `Event` column displays the number of played matches, the `Win` column displays the winned matches and `Loss` the lost ones. The last column `WLRatio` is a Win / Loss Ratio, calculated according to the following formula: `Win / Loss` (if `Loss` ≠ `0`), `Win / 1` (if `Loss` = `0`) and `Loss / -1` (if `Win` = `0`).

In doing so, a high Win / Loss Ratio indicates many wins over little or no losses. A Win / Loss Ratio near 1 indicates more or less as many wins as losses. And, a negative low Win / Loss Ratio indicates many losses over little or no wins.

<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:48:12 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Club </TH> <TH> Initial </TH> <TH> Final </TH> <TH> Performance </TH> <TH> Event </TH> <TH> Win </TH> <TH> Loss </TH> <TH> WLRatio </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Charpilloz, Nicolas (BIE) </TD> <TD> BIE </TD> <TD align="right"> 120.79 </TD> <TD align="right"> 154.98 </TD> <TD align="right"> 0.28 </TD> <TD align="right">  16 </TD> <TD align="right">  15 </TD> <TD align="right">   1 </TD> <TD align="right"> 15.00 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Cavaleri, Franco (PUI) </TD> <TD> PUI </TD> <TD align="right"> 107.28 </TD> <TD align="right"> 143.77 </TD> <TD align="right"> 0.34 </TD> <TD align="right">  14 </TD> <TD align="right">  13 </TD> <TD align="right">   1 </TD> <TD align="right"> 13.00 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Knight, Stuart (ALC) </TD> <TD> ALC </TD> <TD align="right"> 215.28 </TD> <TD align="right"> 249.17 </TD> <TD align="right"> 0.16 </TD> <TD align="right">  14 </TD> <TD align="right">  13 </TD> <TD align="right">   1 </TD> <TD align="right"> 13.00 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Buffet, Vincent (ALC) </TD> <TD> ALC </TD> <TD align="right"> 232.42 </TD> <TD align="right"> 262.58 </TD> <TD align="right"> 0.13 </TD> <TD align="right">  13 </TD> <TD align="right">  12 </TD> <TD align="right">   1 </TD> <TD align="right"> 12.00 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Etienne, Fabrice (COL) </TD> <TD> COL </TD> <TD align="right"> 143.04 </TD> <TD align="right"> 157.85 </TD> <TD align="right"> 0.10 </TD> <TD align="right">  10 </TD> <TD align="right">  10 </TD> <TD align="right">   0 </TD> <TD align="right"> 10.00 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Collazo, Javier (MAR) </TD> <TD> MAR </TD> <TD align="right"> 127.93 </TD> <TD align="right"> 167.60 </TD> <TD align="right"> 0.31 </TD> <TD align="right">  10 </TD> <TD align="right">   9 </TD> <TD align="right">   1 </TD> <TD align="right"> 9.00 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Kaempf, Marc-Olivier (MAR) </TD> <TD> MAR </TD> <TD align="right"> 164.74 </TD> <TD align="right"> 189.61 </TD> <TD align="right"> 0.15 </TD> <TD align="right">  10 </TD> <TD align="right">   9 </TD> <TD align="right">   1 </TD> <TD align="right"> 9.00 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Raetzo, Johnny (SEN) </TD> <TD> SEN </TD> <TD align="right"> 103.02 </TD> <TD align="right"> 116.76 </TD> <TD align="right"> 0.13 </TD> <TD align="right">   9 </TD> <TD align="right">   8 </TD> <TD align="right">   1 </TD> <TD align="right"> 8.00 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Elyan, Rady (CCG) </TD> <TD> CCG </TD> <TD align="right"> 164.99 </TD> <TD align="right"> 182.78 </TD> <TD align="right"> 0.11 </TD> <TD align="right">   9 </TD> <TD align="right">   8 </TD> <TD align="right">   1 </TD> <TD align="right"> 8.00 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Lopez, Andres (GRS) </TD> <TD> GRS </TD> <TD align="right"> 309.47 </TD> <TD align="right"> 343.52 </TD> <TD align="right"> 0.11 </TD> <TD align="right">   9 </TD> <TD align="right">   8 </TD> <TD align="right">   1 </TD> <TD align="right"> 8.00 </TD> </TR>
   </TABLE>
<br>


#### **Players you don't really want in your teams...**

Subsequently, the top-10 worst performers in interclubs encounters, according to the Win / Loss Ratio, are shown in the following table:


<!-- html table generated in R 3.1.1 by xtable 1.7-3 package -->
<!-- Sun Sep  7 17:48:12 2014 -->
<TABLE border=1>
<TR> <TH>  </TH> <TH> Player </TH> <TH> Club </TH> <TH> Initial </TH> <TH> Final </TH> <TH> Performance </TH> <TH> Event </TH> <TH> Win </TH> <TH> Loss </TH> <TH> WLRatio </TH>  </TR>
  <TR> <TD align="right"> 1 </TD> <TD> Chauvet, Laurent (YVE) </TD> <TD> YVE </TD> <TD align="right"> 99.81 </TD> <TD align="right"> 88.58 </TD> <TD align="right"> -0.11 </TD> <TD align="right">  10 </TD> <TD align="right">   0 </TD> <TD align="right">  10 </TD> <TD align="right"> -10.00 </TD> </TR>
  <TR> <TD align="right"> 2 </TD> <TD> Marmo, Xavier (YVE) </TD> <TD> YVE </TD> <TD align="right"> 72.58 </TD> <TD align="right"> 68.08 </TD> <TD align="right"> -0.06 </TD> <TD align="right">  10 </TD> <TD align="right">   0 </TD> <TD align="right">  10 </TD> <TD align="right"> -10.00 </TD> </TR>
  <TR> <TD align="right"> 3 </TD> <TD> Monney, Maël (PAY) </TD> <TD> PAY </TD> <TD align="right"> 20.99 </TD> <TD align="right"> 18.66 </TD> <TD align="right"> -0.11 </TD> <TD align="right">   8 </TD> <TD align="right">   0 </TD> <TD align="right">   8 </TD> <TD align="right"> -8.00 </TD> </TR>
  <TR> <TD align="right"> 4 </TD> <TD> Seitzinger, Harry (ATL) </TD> <TD> ATL </TD> <TD align="right"> 167.82 </TD> <TD align="right"> 163.80 </TD> <TD align="right"> -0.02 </TD> <TD align="right">   7 </TD> <TD align="right">   0 </TD> <TD align="right">   7 </TD> <TD align="right"> -7.00 </TD> </TR>
  <TR> <TD align="right"> 5 </TD> <TD> Jardillier, Patrice (MEY) </TD> <TD> MEY </TD> <TD align="right"> 98.46 </TD> <TD align="right"> 98.46 </TD> <TD align="right"> 0.00 </TD> <TD align="right">   7 </TD> <TD align="right">   0 </TD> <TD align="right">   7 </TD> <TD align="right"> -7.00 </TD> </TR>
  <TR> <TD align="right"> 6 </TD> <TD> Walzer, Fabienne (GRS) </TD> <TD> GRS </TD> <TD align="right"> 84.19 </TD> <TD align="right"> 82.72 </TD> <TD align="right"> -0.02 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> -6.00 </TD> </TR>
  <TR> <TD align="right"> 7 </TD> <TD> Labeydh, Aziz (CTG) </TD> <TD> CTG </TD> <TD align="right"> 105.54 </TD> <TD align="right"> 104.24 </TD> <TD align="right"> -0.01 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> -6.00 </TD> </TR>
  <TR> <TD align="right"> 8 </TD> <TD> Perruchoud, James (SIO) </TD> <TD> SIO </TD> <TD align="right"> 59.47 </TD> <TD align="right"> 59.30 </TD> <TD align="right"> -0.00 </TD> <TD align="right">   6 </TD> <TD align="right">   0 </TD> <TD align="right">   6 </TD> <TD align="right"> -6.00 </TD> </TR>
  <TR> <TD align="right"> 9 </TD> <TD> Coelingh, Gert-Jan (MEY) </TD> <TD> MEY </TD> <TD align="right"> 25.89 </TD> <TD align="right"> 25.89 </TD> <TD align="right"> 0.00 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right">   5 </TD> <TD align="right"> -5.00 </TD> </TR>
  <TR> <TD align="right"> 10 </TD> <TD> Juillard, Richard (SIO) </TD> <TD> SIO </TD> <TD align="right"> 17.64 </TD> <TD align="right"> 17.60 </TD> <TD align="right"> -0.00 </TD> <TD align="right">   5 </TD> <TD align="right">   0 </TD> <TD align="right">   5 </TD> <TD align="right"> -5.00 </TD> </TR>
   </TABLE>
<br>

#### **Top performers for interclubs**

The following chart shows the top performing clubs for the interclubs encounters, i.e. the number of earned points over the season over the initial rankings. The performance is expressed in raw figures and not in percent:

![plot of chunk perfbyclubinter](figure/perfbyclubinter.png) 


#### **Floating or sinking?**

The following chart displays the clubs according to their Win / Loss Ratio, calculated at the clubs' levels, as done for the individual players' levels. Again here, clubs with a Win / Loss Ratio above 1 have won more encounters than lost ones. And symmetrically, those with a ratio below 1, have lost more than won encounters. The vertical dotted line marks the "sea-level" limit of 1.

![plot of chunk wlratiobyclubinter](figure/wlratiobyclubinter.png) 


#### **Above sea level?**

This chart is quite similar to the previous one, as it displays a relationship between the wins and losses, but also, the size of the bubble indicates the volume of played matches. The bigger the bubble, the more played matches, and vice-versa. Again here, the diagonal dotted line, representing a line with `intercept` = `0` and `slope`= `1`, shows whether clubs had more wins than losses if above the line, or more losses than wins if below the line.

![plot of chunk winslossesevents](figure/winslossesevents.png) 

---


### Summary

This study has been realised in `R` and `R Markdown`using the `RStudio` Integrated Development Environment. The main packages used for this data analysis are: `dplyr`, `ggplot2`, `reshape2` and, of course, `knitr`.

Now that the **SR** 2014-2015 season is about to start, may this study's analyses and insights contribute to clubs managers, licensed players and interclubs team captains to adjust their tactics for a successful season.
