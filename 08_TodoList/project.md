Todo List Application

<br>

This is a web app built using webpack which allows the user to create multiple todo lists, called projects, each with their own items. Each todo item can have low, medium, or high priority, with colour coding to represent each (green, blue, and red). Each task also has an optional due date, and tracks whether it is complete using a checkbox, with the projects page also showing when the soonest due date of an incomplete task in each project is.

Each todo list item can also be clicked to enter a details page, which can display an optional description for the item, along with all other information about it displayed as text, except for a checkbox displaying whether it is complete.

I store all data in in ProjectData.js, which exports a DataAccess object with methods for adding, retrieving, and modifying projects and todo list items. Navigation is handled through a single PageLoader which tells each page to load, with navigation event listeners added to projects and items when they are built.

I used the browser's local storage functionality to store the user's projects in a JSON format, which is then loaded if present, and stored in ProjectData.js when the user visits the site again. If the user has no saved projects then the page creates one named "Todo List" with one task called "Create todo list".

projects.png - shows what the list of the user's projects looks like.
todo.png - shows a single project's todo list page.
details.png - shows what the details page for an individual todo list item looks like. 

<br>

GitHub repository: https://github.com/MilesRigby/odin-todo-list

GitHub pages link: https://milesrigby.github.io/odin-todo-list/