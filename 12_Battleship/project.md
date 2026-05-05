## Battleship

<br>

In this project I initially created a couple of object factories using test-driven development, and then moved away from this to create the UI integration, as I haven't learned to perform testing for UI components yet.

The objects built with TDD are a Ship and GameBoard. A Ship is a small object that has a defined size and keeps track of how many times its "hit()" function has been called. It also has an isSunk() function that returns whether it has been hit a number of times equal to its size, as in Battleship a ship is destroyed when all of its tiles have been hit. As this Ship object doesn't track individual parts of the ship, it can't check for when a tile is hit more than once, so this needs to be prevented by other processes. Ships are tested in ship.test.js.

A GameBoard object holds the state of a 10*10 board, using integers to track what has happened to each tile - 0 initially, positive numbers for tiles containing ships, -1 for misses, and -2 for hits. Boards can have ships added to them in order of n=1, 2, 3..., adding the integer value to a specified part of the game board using a starting tile, a ship length, and one one of the four cardinal directions. These ships are stored in an array at index n-1. The object has a method to return the full state of the board at any time.

The board also has a method for receiving attacks, where the board checks the state of the tile being targeted and either rejects the attack if the tile has been targeted before (state -1 or -2), or updates the space, calling hit() on a ship if one is present. Finally, the board has a method allSunk(), which calls isSunk() on each ship to determine if a player has lost the game.

For aiding with testing, the GameBoard factory takes in the Ship factory via dependency injection, allowing testing to mock ship objects and test functionality requiring them. This is used in gameBoard.test.js to define the boards' behaviour.

The game loop uses two Player objects, which are simple containers holding a GameBoard and a type which states whether they are a computer or human player. Since these objects do not have their own behaviour, only storing references to data and another fully tested object, they have no Jest testing associated with them.

<br>

JavaScript for HTML Construction.

A useful addition to my UI setup from previous projects is related to how I have implemented the hiding of players' ships when it is not their turn, or hiding computer players' ships from human players. Where most element attributes either must (e.g. innerText) or can be applied using `element.attribute = value` to modify them in JavaScript, data- attributes require use of `element.setAttribute("attribute", value)`. I have added an if statement to the HTML content builder from project 10 and used it here as well. This can potentially be expanded in future with an object describing the types of attributes that require this syntax (such as aria attributes) as needed.

<br>

When I moved to building the UI, as I believed this project was to be focussed on TDD, I didn't think enough about how to design the UI logic. As I initially thought the UI would be relatively simple, I built all DOM content in a single file, pageContent.js, and made most of it invisible at any given time, with only the players' game boards and names being permanently active on-screen. This was an error which resulted in some rather complex and confusing logic in the game's main event loop, which was also heavily coupled with the UI elements.

I set up the events system to use the pageContent.js's contentObject to trigger different parts of the UI, resulting in a lot of back and forth between them where the event loop would open a UI element and wait for the component to do something before continuing. The event loop also performs significant setup on the UI, passing its own functions to the content object for its UI elements to call when interacted with later.

These issues are extensive and I plan to largely rebuild the UI using an events system, e.g. a PubSub, which will allow both better separation of logic from UI, and enable use of TDD for the game's main event loop via mocking a dependancy-injected events system. I will also split the UI content into several files, each defining a specific dynamic (i.e. only sometimes visible) UI element's behaviour. I also intend to reorganise the CSS of this project into multiple files, and hopefully update it to produce a cleaner UI.

The following is a link to the GitHub repository at a point in its history prior to these changes: https://github.com/MilesRigby/odin-battleship-project/tree/7d702bd86d2d7669dd741b7626d03ad8e7191e26

<br>

GitHub repository: https://github.com/MilesRigby/odin-battleship-project/tree/main

GitHub pages link: https://milesrigby.github.io/odin-battleship-project/