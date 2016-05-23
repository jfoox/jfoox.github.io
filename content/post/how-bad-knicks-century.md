+++
date = "2016-05-19T16:06:42-04:00"
draft = false
title = "How bad have the Knicks been this century?"
icon = "/img/basketball.png"
icontwo = "/img/python.png"
categories = [ "project" ]
projecttitle = "Cumulative Win/Loss Analysis"
projectimage = "/img/thumbnail_winloss.png"
projectdesc = "The Knicks have been one of the more inept NBA franchises this century – but have they been the worst? Using cumulative records, roster turnover, and salary spent, I researched this question."

+++

All statistics courtesy of <a href="http://www.basketball-reference.com" target="_blank">basketball-reference.com</a>.

The New York Knicks have a reputation for ineptitude. They have not won a national championship since 1973; they have won only two playoff series in this millennium; they blundered their way through a sexual harassment lawsuit for which they still deny wrongdoing; and their owner is as bad as his job as he is tone deaf to the world surrounding him.

Setting aside their odious management, the Knicks on the court have been downright bad. After a run of competitiveness throughout the 90s, the team has struggled to compete. Momentary glimpses of hope—trading for Stephon Marbury in 2003, signing Amare Stoudemire in 2010, Linsanity in 2012, setting three point records in a 54-win 2013-14 season—have been just as quickly dashed, respectively including shipping out Keith Van Horn, the meeting of Amare’s fist with a Miami fire extinguisher, the shocking decision not to match Houston’s offer sheet for Jeremy Lin, and trading for Andrea Bargnani, arguably one of the worst trades in NBA history.

But the Knicks reside in New York, a city reputed for its histrionics and ethnocentrism. Knicks fans might claim that they’ve had it worse than any NBA team’s fans, but would they be right? Have the Knicks been the worst team in the league sine their fall from relevance at the turn of the century? To investigate, I took a look at seasonal data since the 1999-00 NBA season, courtesy of <a href="http://www.basketball-reference.com" target="_blank">basketball-reference.com</a>.

To do so, I mined all data using custom written Python scripts, and visualized all data using the pandas library built on MATLAB. In fact, this project was my catalyst for learning pandas—after all, what better way to learn this library than by using it to research the Knicks and depress the hell out of myself?

I first scraped win/loss records for every team over the past 16 seasons, including this season through ~68 games. A simple cumulation plot shows how teams have fared over that timeframe:

<center>
<figure>
    <img src="/img/cum_winloss.png"  />
</figure>
</center>

As it turns out, the Knicks, although towards the bottom with -183 win differential (average of 11.2 games under .500, or 35.5 wins per year), were not the absolute worst cumulatively. That honor belongs to the Washington Wizards, with a whopping -248 win differential, and an average of 15.5 games under .500, or 33.25 wins per year. This came as somewhat of a surprise, given that the team managed to make the playoffs for four years in a row in the mid 2000s, during their DeShawn Stevenson/Agent Zero/LeBron James trash talking triangle heyday. However, their best season in that stretch only totaled 45 wins, and they had not come anywhere near that mark until very recently.

Also below the Knicks were the Charlotte Hornets/Bobcats(/Hornets again), who notably suffered the worst regular season in terms of winning percentage when they went 9-53 in a lockout-shortened 2011 season, and the Minnesota Timberwolves, who have suffered an abysmal stretch since reaching the Western Conference Finals in 2004.

However, of note is that each of these teams is in a significantly better position to compete going forward than New York. The Wizards are currently two games out of 8th place and a third straight playoff berth, the TImberwolves are building a core around a pair of first-overall picks in Andrew Wiggins and Karl-Anthony Towns, and the Charlotte Hornets have won 17 of their past 21 games, quickly becoming a dark horse favorite in the Eastern Conference. Teams whose nadirs fell well below the Knicks’ in previous seasons but who have since leapfrogged them are similarly better off, including the Golden State Warriors and the Los Angeles Clippers.

One sticking point for Knicks fans is the endless turnover of the roster. No team going into training camp on any given October resembles much of the team that came into camp a season prior. The lack of continuity has been cited as a persistant source of the team’s struggles. However, plotting turnover rate—measured by the roster of all players used in a full season compared to the season beforehand—reveals that the Knicks are not the worst culprits here, either:

<center>
<figure>
    <img src="/img/_turnover2000.png"  />
</figure>
</center>

Teams with more turnover include franchises who have consistently struggled but for brief stretches like the Knicks, including New Jersey/Brooklyn, the Clippers, Cleveland, Philadelphia, Houston, Atlanta, Toronto, and Phoenix. Interestingly, although successful teams like the Spurs and Lakers fall towards the bottom, that end of the spectrum does not well predict the best teams over the same stretch, as the Pacers and Jazz have had the least turnover. High turnover rate is a better predictor of failure than low turnover rate is a predictor of success.

Perhaps roster turnover over such a long stretch is meaningless, given the relatively short average span of a player’s career. Recently, a statistic floated around that Carmelo Anthony has had 70 teammates since joining the Knicks five years ago. Presumably, creating a winning environment for him should have entailed roster stability, and the Knicks ought to have had some of the least turnover since trading for Carmelo. Looking at the numbers tells otherwise:

<center>
<figure>
    <img src="/img/_turnover2012.png"  />
</figure>
</center>

In fact, since Carmelo Anthony joined the Knicks, they have had one of the highest rates of turnover. Of the teams above them, only one arguably has a player that can be a core part of a championship team, and that would be the Dallas Mavericks with Dirk Nowitzki. In their case, they have swung big and struck out in free agency as they have tried to retool around him in the twilight of his career. The other groups, including Boston, Phoenix, and the “Trust the Process” Sixers, are in the midst of serious rebuilds. On the other end of the spectrum are teams like the Spurs, Warriors, and Thunder, who are built in win-now modes with rosters capable of winning a championship. (Interestingly, there are also teams like the Pacers, Bulls, and Nuggets, whose reasons for slow turnover are unclear.) In either event, few teams like the Knicks, who have had a championship-capable piece for so long, tend to continuously rebuild.

Last, but certainly not least, if there is one thing the Knicks are unequivocally known for, it’s spending money. From the Allan Houston $100M contract, to the Amare Stoudemire $100M contract, and so many in between, New York has not shied away from pouring cash at their problems. Unfortunately, spending has not translated into success. An analysis at cost per win reveals that no one even comes close to New York:

<center>
<figure>
    <img src="/img/_costperwin.png"  />
</figure>
</center>

So don’t fret, Knicks fans. Your team may not have had the absolute worst win/loss differential, but they have had the fourth worse, and they are in a worse position than the three below them. Your team may not have had the highest rate of turnover, but they have had an unusually high rate for a team with a championship-caliber player. And your team has certainly been willing to spend the most amount of money for the least rate of return. At just over $2.5M spent per win, and with no other team even crossing $2M per win (not even the Prokhorov Nets!), the Knicks smoke their competition—likely using an enflamed $100 bill as a lighter. All this combined, if the Knicks haven’t been the worst team of the century, there is certainly a case to be made for them to be near the very bottom.