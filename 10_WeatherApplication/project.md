## Weather Web App

<br>

I created this project using an older version of my webpack-base repository as a template, which does not have Jest testing available.

This is my first project to make use of an API, specifically the Visual Crossing Weather API. src/API-control contains the files for building an API call given a user location request, retrieving only the data needed for the site's UI, and processing that data into a desired object format for the rest of the program. The bulk of the call is defined in a JavaScript object, APICallDesc, which is then parsed into a complete URL when the user makes a request. This allows each part of the request to be modified independantly within a structured format.

I display daily weather data using a horizontally scrolling window of cards, using clickable arrows to move the cards side-to-side, displaying the next two weeks (15 days including the current date) of data. Various information like high and low temperature for the day, cloud coverage and rain, as well as safety information like UV index and visibility, are displayed. I set up each date's display card to open a second scrolling window when clicked, which displays a smaller amount of hourly data for the full 24 hours of that day.

src/Pages/weatherDisp/schema.js defines the data that is displayed on each of the daily and hourly data cards, as well as determining units, making it easy to find and fix these or add to them if something about the displays needs to change, though styles and the API call would need to be updated separately if weather data is added/removed.

I have also used a function to define the scale of the scrolling windows, which defaults to 0.45rem, but grows or shrinks to match particularly narrow or wide screens. This means that for arbitrarily small or large screen sizes, the number of days and hours that are displayed on-screen at a given time is roughly clamped between two values, e.g. 2 and 7 for daily data. This allows the UI to work on almost any size screen, though while useable does look slightly clunky on mobile.

daily.png and hourly.png show the site with just the daily weather displayed, and after clicking on of the days (26/04/2026) to display the hourly data, with each view scrolled a bit to the right.

<br>

## Detatched DOM Tree Construction.

A significant improvement I made in this project over previous ones is in the simplicity of creating DOM content in JavaScript. Writing out the creation of each object and adding each of their attributes and children in turn is a long-winded process and often makes debugging difficult. I previously solved this by writing a UI element into HTML.template, adding styles, and seeing how it looked. I would debug during this process and then rewrite it line-by-line into JavaScript. I wanted to create a way to create these elements in javaScript in a way that read more like natural HTML.

src/Pages/ContentBuilder.js contains a function which takes in a JavaScript object with a particular format and outputs a detatched DOM tree for modification or insertion into the DOM/another detatched tree. I tried to match the format of these objects as closely as possible to standard HTML, making creating elements in JavaScript much quicker and easier, as you can see the final structure as you write the objects. This is done by making each element its own JavaScript object with the element type as the key, followed by an object for attributes (key-value pairs are the name and value of each desired attribute), and a list of children which can each be on a new line and indented to match standard HTML syntax.

The main differences include requiring innerText or textContent to add text to elements rather than placing text between tags, and class is renamed className due to class being a keyword in JS, though JS does allow symbols HTML doesn't to be explicitly written out (e.g. \&lt; vs <).

<br>

An example of the syntax from this project is shown below:

Standard HTML:

```
<div id = "daily-weather-disp", class = "horizontal-scroll-window">
    <div class = "scrollview-left scrollview-button">
        <p>&lt;</p>
    </div>
    <div class = "scrollview-right scrollview-button">
        <p>&gt;</p>
    </div>

    <div class = "scrollview-items"></div>
</div>
```
<br>

My object syntax:

```
{"div": { attributes: {"id": "daily-weather-disp", "className": "horizontal-scroll-window"},children: [
    { "div": { attributes: {"className": "scrollview-left scrollview-button"}, children: [
        { "p": { attributes: {"innerText": "<"}, children: []}}
    ]}},
    { "div": { attributes: {"className": "scrollview-right scrollview-button"}, children: [
        { "p": { attributes: {"innerText": ">"}, children: []}}
    ]}},

    { "div": { attributes: {"className": "scrollview-items"}, children: []}}
]}};
```

<br>

GitHub repository: https://github.com/MilesRigby/odin-weather-app/blob/main/src/styles.css

GitHub pages link: https://milesrigby.github.io/odin-weather-app/