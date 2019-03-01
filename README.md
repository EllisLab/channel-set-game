# Game Channel Set

Quickly create a Game Channel in your ExpressionEngine install with this Channel Set.

The Game Channel Set comes with three Channels and custom fields to get you up and running fast. Here’s what’s inside:

## Game Channel

### Custom Fields

* game_location}: a Text field for the location of the game
* {game_start_time}: a Date field for the official start time of the game
* {game_teams}: a Grid field to select which teams are playing in the game  
  * :team - a Relationship to the Teams Channel  
  * :location - Indicator for whether this team is playing as Home/Away

## Player Channel

### Custom Fields

* {player_biography}: a Textarea for the a player’s bio
* {player_eligible}: a Toggle field to indicate if the player is eligible to play, or is injured or otherwise ineligible
* {player_height}: Text field for the player’s height
* {player_hometown}: a Text field for the player’s hometown
* {player_position}: a Text field for the player’s field position
* {player_weight}: Text field for the player’s weight

###Team Channel

### Custom Fields

* {team_history}: a Textarea for the team’s history
* {team_home_field}: a Text field for the name of the team’s home field
* {team_homepage}: a URL field for the team’s website
* {team_mascot}: a Text field for the team mascot’s name
* {team_roster}: a multiple Relationship to the Player channel

## Nafai

```
{exp:channel:entries channel='game' limit='1' require_entry='yes'}
	{if no_results}
		{redirect='404'}
	{/if}

	<h1>{title}</h1>

	<p>{game_location} on {game_start_time format='%D, %F %d, %Y - %g:%i'}</p>

	<h2>
		{game_teams}
			{game_teams:team}{game_teams:team:title}{/game_teams:team} ({game_teams:location})
			{if game_teams:count < game_teams:total_rows}vs.{/if}
		{/game_teams}
	</h2>

	{game_teams}
		{game_teams:team}
			<h3><a href="{game_teams:team:team_homepage}">{game_teams:team:title}</a></h3>

			{game_teams:team:team_history}

			<h4>Roster</h4>
			<ul>
				{game_teams:team:team_roster}
					<li {if ! game_teams:team:team_roster:player_eligible}class="ineligible"{/if}>
						<b>{game_teams:team:team_roster:title}, {game_teams:team:team_roster:player_position}</b><br>
						<i>{game_teams:team:team_roster:player_height}, {game_teams:team:team_roster:player_weight}</i><br>
						From: {game_teams:team:team_roster:player_hometown}
					</li>
				{/game_teams:team:team_roster}
			</ul>
		{/game_teams:team}
	{/game_teams}
{/exp:channel:entries}
```

## License

Copyright (C) 2004 - 2016 EllisLab, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL ELLISLAB, INC. BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Except as contained in this notice, the name of EllisLab, Inc. shall not be used in advertising or otherwise to promote the sale, use or other dealings in this Software without prior written authorization from EllisLab, Inc.
