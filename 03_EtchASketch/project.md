## Etch-A-Sketch

<br>

For this project I created a functional, though bare-bones, UI, allowing a user to draw pixelated images by hovering their mouse over a grid (made using flex boxes) in either black-and-white, or colour modes, using JavaScript to alter css styles. This results in the drawing of continuous lines as long as the mouse doesn't move too quickly, akin to the lines of an etch-a-sketch.

Mousing over a grid cell increases the opcity in 0.1 increments, gradually creating a darker colour with repeat mouseovers. In colour mode, which is the default, each mouseover also generates a random colour representing the colour the cell would have with an opacity of 1. Switching to black-and-white with colours present will keep the current colours but continue increasing their opacity.

I create these grids using a JavaScript function that builds an n*n grid of div elements, where 1 $\leq$ n $\leq$ 100, and adds an event listener to each cell to change the opacity when the mouse enters it.

There are also two buttons, the first of which allows the user to create a new empty grid of a specified size, for which I use a prompt to get user input. The second button is a toggle which switches between the black-and-white and colour modes.

page.png shows some lines on a 50*50 grid, both in black-and-white and colour, with some different shades.

<br>

GitHub repository: https://github.com/MilesRigby/Odin-etch-a-sketch/tree/main

GitHub pages link: https://milesrigby.github.io/Odin-etch-a-sketch/