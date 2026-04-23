## Tic Tac Toe/Naughts & Crosses

<br>

In this project I developed a cleaner UI of my own using the skills developed in previous projects, including box-shadows to create visual depth, and used JavaScript to implement a simple turn-based system for gameplay between two opponents.

I used a publisher/subscriber events system, enabling me to more easily write cleaner code, and immediately invoked function expressions (IIFEs) to create objects with factory functions. This makes use of closures to only expose functionality that needs to be public. Most public functionality in this project is functions subscribed to the event system.

This resulted in much easier to follow code than in previous projects, with a clean seperation between state and UI, using seperate board object, turn tracking, board UI updates, and button/form managers.

There is also the option for players to use a form to set their names at any time, which operates independantly of the main game loop. Names are then displayed in the turn indicator and on victory screens.

page.png shows how the site appears at game end on my monitor.

<br>

GitHub repository: https://github.com/MilesRigby/odin-tic-tac-toe

GitHub pages link: https://milesrigby.github.io/odin-tic-tac-toe/