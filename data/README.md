
Cleaned csv files for the tracking data from the Big Data Cup (data found [here](https://github.com/bigdatacup/Big-Data-Cup-2021)).

You can check out what CAN-USA P1 PP1 looks like [on my Twitter](https://twitter.com/the_bucketless/status/1508884825792425984).

Things I'm updating:
<ul>
  <li>Adding a column for video shots. Probably more useful for me than you. A video shot is a continuous view of the game from one camera. The model can only determine where on the ice the action is happening from the center ice camera, so anything else gets cut out. When the game leaves and then returns to the center ice camera, everything gets reset. As a result, the values in track_id are not unique to a single player. To make them unique, we can group by track_id and video_shot.</li>
  <li>Adjusting all coordinates up and to the left (https://twitter.com/the_bucketless/status/1508478054175154177).</li>
  <li>Occasionally touching up coordinates beyond that.</li>
  <li>Adding goalie jersey numbers. It's rare that I'll do this for any other player, but I think it's important to keep track of which one of them is the goalie.</li>
  <li>Removing tracks that aren't around for more than 6 frames. These are often what I've taken to calling phantoms (false positives from the object detection model). This will occasionally remove a legitimate track, but if the player's around for less than a 5th of a second, I think we can ignore them.</li>
  <li>Removing any other phantoms that come up.</li>
  <li>Merging track_id values representing the same player when within a few frames of each other.</li>
  <li>Imputing coordinates for players if they go missing for a few frames.</li>
</ul>

I've also removed video shot 3 from CAN_USA P1 PP2. It was too much work to try to fix that one. It's only 11 seconds and none of in the ozone, so not a big loss.
