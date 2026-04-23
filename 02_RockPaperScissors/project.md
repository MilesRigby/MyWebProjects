## Rock Paper Scissors Application

<br>

This project is part of the introduction to JavaScript from _The Odin Project_'s _Foundations_ course, used to create a small interactive game with code and UI integration - Rock Paper Scissors played against a random opponent. Each game is won by the first to five points.

I used HTML buttons to allow the user to select their moves, with javascript adding event listeners to trigger each round when these are clicked. Switch statements define much of the conditional logic, with if/else statements for binary pass/fail checks.

I also used Javascript to create new HTML paragraph elements and insert them at the bottom of a reversed flex box, which report each round's results as well as game wins. This results in a series of messages which moves down the page as new messages are added to the top visually. web.png shows the page after a few rouds have been played.

The JavaScript also contains legacy code in the form of the function "playGameConsole()" as opposed to the UI-driven "playGameWebsite()" which the program runs automatically to set up the button events. Originally written for a local console, this can still be run manually in the browser console, and uses alerts to allow the user to manually type in their choices. This version runs until a total of five points rather than first to five.

There are a couple of issues with the console version, which are that invalid inputs silently fail and no round results are reported until the whole game ends. alerts_pre.png and alerts_post.png show the page before and after the end of a game played with the console function.

<br>

GitHub repository: https://github.com/MilesRigby/odin-rps-console-game

GitHub pages link: https://milesrigby.github.io/odin-rps-console-game/