
Cleaned csv files for the data from the Big Data Cup (data found [here](https://github.com/bigdatacup/Big-Data-Cup-2021)).

You can check out what CAN-USA P1 PP1 looks like [on my Twitter](https://twitter.com/the_bucketless/status/1508884825792425984).

<br/>
<h1>Play-by-play data</h1>
The only addition to the play-by-play file is two frame ID columns. These can be used to identity which frame in the tracking data an event is associated with. The second frame ID is used exclusively on passing plays to denote in which frame the pass was received. This was mainly done because I didn't like having invisible players receiving passes.  
<br/><br/>
I've also corrected a few errors where I've seen them.

<br/><br/>
<h1>Tracking data</h1>
A couple notes:
<ul>
  <li>If coordinates look a little choppy somewhere, that's almost certainly my fault.</li>
  <li>When playing with the files, consider the coordinates to be an area as opposed to a specific point. A goalie's positioning can be affected by their stance and players who fall can look like they're moving much faster than everyone else.</li>
</ul>  

<br/><br/>
Things I'm updating:
<ul>
  <li>Adding a column for video shots. Probably more useful for me than you. A video shot is a continuous view of the game from one camera. The model can only determine where on the ice the action is happening from the center ice camera, so anything else gets cut out. When the game leaves and then returns to the center ice camera, everything gets reset. As a result, the values in track_id are not unique to a single player. To make them unique, we can group by track_id and video_shot. This can also be used to determine which coordinates relate to the end of one play and which are for the ensuing faceoff when they occur at the same time in the game. Faceoffs will be at the start of a video shot.</li>
  <li>Adding a column for game seconds to make it easier to merge with the play-by-play data.</li>
  <li>Adjusting all coordinates up and to the left (https://twitter.com/the_bucketless/status/1508478054175154177).</li>
  <li>Occasionally touching up coordinates beyond that.</li>
  <li>Setting tracks to the correct team.</li>
  <li>Setting jersey numbers for goalies and players.</li>
  <li>Removing false positives from the object detection model.</li>
  <li>Merging track_id values representing the same player when within a few frames of each other.</li>
  <li>Imputing coordinates for players if they go missing for a few frames.</li>
</ul>

<br/><br/>
Files skipped:
<ul>
  <li>ROC FIN P2 PP3 - too short to bother with.</li>
  <li>ROC FIN P2 PP4 - too short to bother with.</li>
  <li>USA FIN P3 PP6 - about 12 seconds of 6v5 time.</li>
</ul>

<br/><br/>
Things I've removed:
<ul>
  <li>Video shot 3 from SUI ROC P1 PP1 - last 4 seconds of the powerplay.</li>
  <li>Video shot 2 from USA FIN P2 PP3 - 4 seconds near the end of the powerplay.</li>
  <li>Video shot 3 from SUI CAN P2 PP4 - last 2 seconds of the powerplay.</li>
  <li>Video shot 2 from SUI FIN P2 PP5 - this was a replay.</li>
</ul>

<br/><br/>
Things I've handtracked:
<ul>
  <li>Video shot 3 from CAN USA P1 PP2.</li>
  <li>Video shot 3 from CAN USA P2 PP3.</li>
  <li>Parts of video shot 1 from CAN USA P3 PP7.</li>
  <li>Video shot 2 from CAN USA P3 PP7.</li>
  <li>Video shot 5 from CAN USA P2 PP5.</li>
  <li>Video shot 2 from CAN USA P3 PP6.</li>
  <li>Video shot 3 from SUI ROC P1 PP2.</li>
  <li>Video shot 3 from SUI ROC P3 PP3.</li>
  <li>Video shot 2 from SUI ROC P3 PP5.</li>
  <li>Video shot 3 from ROC FIN P2 PP5.</li>
  <li>Video shot 3 from ROC FIN P3 PP6.</li>
  <li>Video shot 2 from USA FIN P2 PP1.</li>
  <li>Video shot 2 from USA FIN P3 PP4.</li>
  <li>Video shot 2 from USA FIN P3 PP5.</li>
  <li>Video shot 5 from SUI CAN P1 PP1.</li>
  <li>Video shot 3 from SUI CAN P1 PP2.</li>
  <li>Video shot 3 from SUI CAN P3 PP5.</li>
  <li>Video shot 2 from SUI FIN P1 PP1.</li>
  <li>Video shot 3 from SUI FIN P1 PP2.</li>
  <li>Video shot 2 from SUI FIN P2 PP3.</li>
  <li>Video shot 2 from SUI FIN P2 PP4 (this was actually from a different camera, but it was in there, so I did it).</li>
  <li>Video shot 5 from SUI FIN P2 PP4.</li>
  <li>Video shot 4 from SUI FIN P2 PP5.</li>
</ul>

<br/><br/>
If checking the changelog directory, note that the first two files are incomplete and the third may be missing information from some manual manipulation of the file.

<br/>
<h1>Rosters</h1>
There was only one player I noticed with an incorrect number (Evelina Raselli). Otherwise, the roster files are the same as the original repo.
