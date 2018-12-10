Examination of Referee Tendencies and Biases in the National Football League
================
Tom Bliss, Connor Daly, Jacob Klein, Patrick Lewis
December 2018

Data for this analysis was collected from the 2013-2014 NFL season through Week 9 of the 2018-2019 NFL season. It should be noted that this analysis was conducted during the 2018-2019 NFL season. Thus we have included all data available for the current season, but this season was excluded in any analyses in which penalties were compared over entire seasons, since all data for the entire season will not be available until February 2019.

We downloaded play-by-play data from [NFL Savant](http://www.nflsavant.com/about.php?fbclid=IwAR3c8IZngQd0eE_0jp3Z401TdZXSBa8E-qEAX8J7J4uC3--CisVr7ZQfjEQ). From this site, we downloaded CSV files from seasons beginning in 2013 through 2018. These six CSV files begin with "pbp" and are located within the "/data" folder of [this repository](https://github.com/JacobK-/referee-visualizations). We then downloaded referee game data from [Pro-Football-Reference](https://www.pro-football-reference.com/officials/index.htm?fbclid=IwAR387n92do_jrcbwKAjKNR2Y_GSGpcnWMGbCbJ7Pwmx7AdpZQRSbmglfSfU).

As noted in the Introduction, because there are hundreds of referees, linesmen, side judges, and line judges employed by the NFL, for the purposes of this analysis we grouped officials by head referee. We also excluded any referee crews that have not been active in the NFL for a sufficient amount of time (and thus do not yield a sufficient number of data points); all referee crews in our dataset have reffed over 50 games between the 2013 NFL Season through week 9 of the 2018 NFL Season, inclusive.

A CSV file is available in the "/data" subfolder for each of the 17 referees we included in the analysis. Also included in this subfolder is a file called "abbreviations.csv" which was used when joining the play-by-play data to the referee data, and includes a mapping of team names to team abbreviations. For example, this file maps team name "Arizona Cardinals" to team abbreviation "ARI".

In additon to the data there is a file entitled preprocessing.R which iterates through the CSV Files and merges them into a single data set. Moreover, since many of the penalty types in our dataset are quite similar in nature (e.g. `Offensive Offside` and `Defensive Offside`), so we grouped such instances using universal grouping terms, as shown in the below table. Moreover, certain penalty type groupings accounted for less than 1% of all observations even after the groupings were applied, and such groups were then grouped again into the `Other` category. The table below highlights all groupings we used for our analysis.

<table>
<colgroup>
<col width="17%" />
<col width="82%" />
</colgroup>
<thead>
<tr class="header">
<th>Grouping Term</th>
<th>Penalty Types Included</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong> Delay of Game </strong></td>
<td>Defensive Delay of Game, Delay of Game, Delay of Kickoff</td>
</tr>
<tr class="even">
<td><strong> Illegal Block </strong></td>
<td>Chop Block, Clipping, Illegal Blindside Block, Illegal Block Above the Waste, Illegal Crackback, Illegal Peelback, Illegal Wedge, Low Block, Offensive Holding</td>
</tr>
<tr class="odd">
<td><strong> Illegal Formation </strong></td>
<td>Illegal Formation, Illegal Motion, Illegal Shift</td>
</tr>
<tr class="even">
<td><strong> Illegal Tackle </strong></td>
<td>Face Mask (15 Yards), Horse Collar Tackle, Lowering the Head to Initiate Contact</td>
</tr>
<tr class="odd">
<td><strong> Illegal Use of Hands </strong></td>
<td>Illegal Use of Hands</td>
</tr>
<tr class="even">
<td><strong> Offside </strong></td>
<td>Defensive Offside, Encroachment, False Start, Neutral Zone Infraction, Offensive Offside, Offside on Free Kick</td>
</tr>
<tr class="odd">
<td><strong> Pass Interference </strong></td>
<td>Defensive Holding, Defensive Pass Interference, Illegal Contact, Offensive Pass Interference</td>
</tr>
<tr class="even">
<td><strong> Roughing a Protected Player </strong></td>
<td>Roughing the Kicker, Roughing the Passer, Running Into the Kicker</td>
</tr>
<tr class="odd">
<td><strong> Too Many Men on the Field </strong></td>
<td>Defensive 12 On-Field, Defensive Too Many Men on the Field, Illegal Substitution, Offensive 12 On-Field, Offensive Too Many Men on Field</td>
</tr>
<tr class="even">
<td><strong> Unsportsmanlike Conduct </strong></td>
<td>Disqualification, Personal Foul, Taunting, Unnecessary Roughness, Unsportsmanlike Conduct</td>
</tr>
<tr class="odd">
<td><strong> Other </strong></td>
<td><strong>Fair Catch Interference:</strong> Fair Catch Interference, Interference with Opportunity to Catch, Kick Catch Interference<br><br><strong>Illegal Action to Block a Field Goal:</strong> Leaping, Leverage<br><br><strong>Illegal Bat:</strong> Illegal Bat<br><br><strong>Illegal Forward Pass:</strong> Illegal Forward Pass<br><br><strong>Illegal Kickoff:</strong> Kickoff Out of Bounds, Short Free Kick<br><br><strong>Illegal Player Out of Bounds:</strong> Illegal Touch Kick, Illegal Touch Pass, Player Out of Bounds on Kick, Player Out of Bounds on Punt <br><br><strong>Ineligible Player Downfield:</strong> Ineligible Downfield Kick, Ineligible Downfield Pass<br><br><strong>Intentional Grounding:</strong> Intentional Grounding<br><br><strong>Invalid Fair Catch Signal:</strong> Invalid Fair Catch Signal<br><br><strong>Tripping:</strong> Tripping</td>
</tr>
</tbody>
</table>

<br> Additionally, due to some teams moving cities as well as general inconsistency of abbreviations across the data, the following abbreviations were updated to ensure consistency in the dataset:

| Team Name | Old Abbreviation | New Abbreviation |
|-----------|------------------|------------------|
| Chargers  | SD               | LAC              |
| Jaguars   | JAC              | JAX              |
| Rams      | LA               | LAR              |
| Rams      | STL              | LAR              |

Finally, the FinalReport.rmd creates the html file of the Final Report located in the "/docs" folder. Also included in this folder are two files which contain code for our interactive component of the report entitled "index.html" and "index\_report.html". The file "index.html" is a stand-alone version of the interactive component while "index\_report.html" is designed to work within the "FinalReport.html" file.
