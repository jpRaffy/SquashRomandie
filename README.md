SquashRomandie
==============


Statistics for Squash Romandie


### Introduction

This study has been conducted during the second half of August 2014. Its purpose is to perform some data analysis on match results for the [Squash Romandie](http://squashromandie.ch) regional league of [squash](http://en.wikipedia.org/wiki/Squash_%28sport%29). **Squash Romandie (SR)** groups together 18 sports clubs mainly focused on squash and located in [Suisse romande](http://en.wikipedia.org/wiki/Suisse_romande), the French-speaking part of Switzerland.

Every season, between the beginning of September and the end of June of next year, official matches, tournaments and interclubs are organised for licensed players of the **SR** organisation. Depending of the matches outcomes, points are awarded to the winning player and deducted from the loosing player's ranking, according of the ranking difference between the 2 players and the score.

The data collected for this study from the [SR](http://squashromandie.ch) website, represents all the results for the 2013-2014 season as of **7 August 2014**.


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
