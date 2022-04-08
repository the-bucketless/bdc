
Cleaned csv files for the tracking data from the Big Data Cup (data found [here](https://github.com/bigdatacup/Big-Data-Cup-2021)).

You can check out what CAN-USA P1 PP1 looks like [on my Twitter](https://twitter.com/the_bucketless/status/1508884825792425984).

A couple notes:
<ul>
  <li>If coordinates look a little choppy somewhere, that's almost certainly my fault.</li>
  <li>When playing with the files, consider the coordinates to be an area as opposed to a specific point. A goalie's positioning can be affected by their stance and players who fall can look like they're moving much faster than everyone else.</li>
</ul>  

Things I'm updating:
<ul>
  <li>Adding a column for video shots. Probably more useful for me than you. A video shot is a continuous view of the game from one camera. The model can only determine where on the ice the action is happening from the center ice camera, so anything else gets cut out. When the game leaves and then returns to the center ice camera, everything gets reset. As a result, the values in track_id are not unique to a single player. To make them unique, we can group by track_id and video_shot.</li>
  <li>Adding a column for game seconds to make it easier to merge with the play-by-play data.</li>
  <li>Adjusting all coordinates up and to the left (https://twitter.com/the_bucketless/status/1508478054175154177).</li>
  <li>Occasionally touching up coordinates beyond that.</li>
  <li>Setting tracks to the correct team.</li>
  <li>Setting jersey numbers for goalies and players involved in play-by-play events.</li>
  <li>Removing tracks that aren't around for more than 6 frames. These are often what I've taken to calling phantoms (false positives from the object detection model). This will occasionally remove a legitimate track, but if the player's around for less than a 5th of a second, I think we can ignore them.</li>
  <li>Removing any other phantoms that come up.</li>
  <li>Merging track_id values representing the same player when within a few frames of each other.</li>
  <li>Imputing coordinates for players if they go missing for a few frames.</li>
</ul>

Things I've removed:
<ul>
  <li>Video shot 3 from CAN USA P1 PP2.</li>
  <li>Video shot 3 from CAN USA P2 PP3.</li>
  <li>Video shot 5 from CAN USA P2 PP5.</li>
  <li>Video shot 2 from CAN USA P3 PP6.</li>
  <li>Video shot 3 from ROC FIN P2 PP5.</li>
  <li>Video shot 3 from ROC FIN P3 PP6.</li>
  <li>Video shot 3 from SUI ROC P1 PP1.</li>
  <li>Video shot 3 from SUI ROC P1 PP2.</li>
  <li>Video shot 3 from SUI ROC P3 PP3.</li>
  <li>Video shot 2 from SUI ROC P3 PP5.</li>
  <li>Video shot 2 from USA FIN P2 PP1.</li>
  <li>Video shot 2 from USA FIN P2 PP3.</li>
</ul>
I'm not ambitious enough to try to work with those right now.  

<br/><br/>
Files skipped:
<ul>
  <li>CAN USA P3 PP7 - it looked like a lot of coordinate adjustments, so I'll come back to this later.</li>
  <li>ROC FIN P2 PP3 - too short to bother with.</li>
  <li>ROC FIN P2 PP4 - too short to bother with.</li>
</ul>

<br/><br/>
If checking the changelog directory, note that the first two files are incomplete and the third may be missing information from some manual manipulation of the file.
