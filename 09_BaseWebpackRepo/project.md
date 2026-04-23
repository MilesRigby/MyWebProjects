## Base Webpack Repository

<br>

This project is not part of _The Odin Project_'s curriculum, however I have found it very useful in initialising new projects much more rapidly. The process of setting up a new webpack project with all the functionality I might need to use can be quite slow, so I wanted to streamline the process by having a barebones project base already setup that I can expand as I'm introduced to new tools.

Initially I included HTML, CSS, and JavaScript functionality in this base, along with a git-ignore for dist and node modules, so some setup is required when starting a new project to install everything. This base has then expanded as I've been introduced to new tools through _The Odin Project_, so far including the recommended ESLint preset, and setup for using the Jest JavaScript testing framework with babel to make it compatable with ESM imports/exports.

Despite it growing, I have generally kept this base as minimal as possible while being rapid to setup new projects with. This is because I don't want to hard-code a particular way all my projects must work that I then need to handle when working on new ones, and can apply the knowledge and skills I gain to as much of each new project as possible. I don't use any permanent code other than importing styles.css in index.js, and minimal boilerplate in HTML.template. Since I create DOM content primarily using JavaScript, the HTML should not need to be modified.

I use this base by setting this repository as a template on GitHub when creating new projects that require webpack. This creates a repository with a main branch identical to the webpack base to build off of. The project's README (also copied over) contains instructions of how to initialise the project to allow starting on the unique coponents of each project quickly. This README's content can then be replaced with information on the new project at any time.

<br>

GitHub repository: https://github.com/MilesRigby/webpack-base/tree/main