---
layout: post
title:  "Schedule-adjusted league table"
date:   2020-09-13 19:23:33 +0200
---
In most soccer leagues, the league table is the standard way to rank teams, and is used at the end of the season to crown champions and choose teams for promotion and relegation, as well as qualification for international competitions. League points are gained by winning or drawing games. However, the table does not take into account the difficulty of opponents; winning against the strongest team in the league is worth as many points as winning against the weakest. As a consequence, the schedule of when teams play each other can skew the ranking of teams in favor of those with easier schedules. This is more of a problem towards the beginning of the season.
The [schedule-adjusted league table (SALT) ][http://statsbomb.com/2018/11/introducing-the-schedule-adjusted-league-table/] was proposed by Constantinos Chappas as a better way to tell how good teams have been doing so far. Basically, for each pair of teams, SALT takes into account the difference in points they have gained from equivalent matchups at the equivalent venue. In doing so, it is able to xxx.

SALT uses a linear model: $$M P = R$$, where $$M$$ is a 190*20 matrix of every matchup times every team, $$R$$ is a vector of relative points, so the difference in points per game for the games that both teams have played, and $$P$$ is vector of how many more points per game the team earns compared to average (will be scaled to points later), to be solved for with least-squares. For additional details, check the original post by Chappas.

SALT has some attractive properties:
- The average of the SALT points is equal to the average of the actual points after each matchday.
- At the end of the season, SALT and the actual league table are equivalent!

Let’s code this model up in R, and look at some results for the 2018-2019 Serie A season.
s



To calculate $$R$$, I will use two helper matrices: one 40*20 matrix of , and another matrix with the same dimensions containing the number of points the row team gained from the match.

To obtain the least-squares solution, I could use lsfit, but in this case I used the Moore-Penrose pseudoinverse (via SVD) instead.



For some other alternative league tables, take a look at:
- [alt-3.uk](https://alt-3.uk/leagues/italy-serie-a/) and the [method](https://alt-3.uk/about/the-maths/)
- [fivethirtyeight](https://projects.fivethirtyeight.com/soccer-predictions/serie-a/) and the [method](https://fivethirtyeight.com/methodology/how-our-club-soccer-predictions-work/)
