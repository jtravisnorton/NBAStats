NBAStats
===

This is a Python module I have put together to make it easier and faster to parse NBA statistics. 

version 1.0.1

My apologies for the lack of documentation within the package and on here.  That will be coming quickly.

To get started, install the module using the following:
```$ easy_install nbastats```
or 
```$ pip install nbastats```

*This module requires the most recent versions of `pandas` and `requests`.*

Once you have `NBAStats` installed, load it into your python environment using:

```python

import nbastats.nbastats as nbastats
```

Once you have the package imported, you can use the following commands to collect data:

<h3>Shot Chart Data</h3>

If you wish to see detailed information on a single players shot chart, use the `ShotChart` method. To use this method, you first need the unique id number of the player you are interested in. You can obtain this by finding the player's profile page on `http://stats.nba.com` and looking in the address bar. You may have to click the "stats" tab when you find the players page. For this example, I'll use Paul George. His NBA ID is `202331`.
```python
george = nbastats.ShotChart('202331')
george.shotchart().head(2)
```
This code returns the following pandas dataframe: 

| index | GRID_TYPE	| GAME_ID | GAME_EVENT_ID | PLAYER_ID | PLAYER_NAME | TEAM_ID | TEAM_NAME | PERIOD | MINUTES_REMAINING | SECONDS_REMAINING | EVENT_TYPE | ACTION_TYPE | SHOT_TYPE | SHOT_ZONE_BASIC | SHOT_ZONE_AREA | SHOT_ZONE_RANGE | SHOT_DISTANCE | LOC_X | LOC_Y | SHOT_ATTEMPTED_FLAG | SHOT_MADE_FLAG |
| :----: | ---- | ---- | :----: | :----: | :----: | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0	| Shot Chart Detail	| 0021300001 | 5 |  202331 | Paul George | 1610612754 | Indiana Pacers | 1 | 11 | 30 | Made Shot | Pullup Jump shot | 2PT Field Goal | Mid-Range | Right Side Center(RC) | 16-24 ft. | 19 | 105 | 164 | 1 | 1 |
| 1	  | Shot Chart Detail | 0021300001 | 16 | 202331 | Paul George | 1610612754 | Indiana Pacers	| 1	| 10 | 11 | Made Shot | Layup Shot | 2PT Field Goal | Restricted Area | Center(C) | Less Than 8 ft. | 1 | -10 | 3 | 1 | 1 |

There are a couple things to note. First, invoking `nbastats.ShotChart('202331')` creates an object that has to unique methods. each of these returns specific data in a `Pandas` dataframe. You can manipulate and adjust all of the data just as you would with a normal `Pandas` dataframe.

####Methods

#####`.shotchart()`
This method of the returns detailed information about all of a players shots that you have chosen. The table above is an example of the type of data that this method returns.

#####`.leagueaverage()`
This method returns a table with league averages for shots taken and made from each of the identified zones on the court. This is not player specific information. It is league specific. If you invoke this method for different players during the same time period, the results should be identical.



`BoxScore`

`GameLog`

`PlayByPlay`

`Lineups`
