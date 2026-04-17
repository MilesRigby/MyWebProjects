Restaurant Homepage

<br>

This project is the first I've built using webpack, requiring deployment to a gh-pages github branch to provide github pages an html entry point (webpack uses index.js). This site is a single page application (SPA), using a small amount of static HTML to create a navigation section, and then loading in each page's content by constructing it in JavaScript, with navigation setup up in index.js. I constructed pages by first writing an outline in HTML, and then converting to JavaScript pages for navigation.

This project has a significantly more complex layout than previous projects, split between a main page, the restaurant's menu, and an about section with contact details. For most content I created placeholders using lorem ipsum, with some custom content to establish a consistent style for the restaurant.

I used images from Unsplash to provide a background restuarant image for the site, and a barbeque for the main page, with a radial gradient to help it blend into the page's background. I also added a double-lined border around each page using a layered box-shadow.

Home.png, Menu_wide.png, and About.png demonstrate the layout of each page as they appear on my monitor.

I also used some responsive design principles for this project, allowing it to display well on a variety of screen sizes. At small screen widths, many items in the menu shoft from being placed side-by-side to stacked on top of eachother, maintaining font size while reducing the number of lines each item description requires by given them more horizontal space.

Menu_narrow_top.png and Menu_narrow_bottom.png show how the layout changes when the browser window is made narrow. The page also becomes much taller than the height of my monitor at this width.

<br>

GitHub repository: https://github.com/MilesRigby/odin-restaurant-homepage

GitHub pages link: https://milesrigby.github.io/odin-restaurant-homepage/