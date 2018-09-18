# Lab 06: Node, npm, Express, and APIs

**NOTE: This is a modified version of the lab 6 instructions. We will add the Weather API functionality in lecture today.**

## Resources

[Node JS Docs](https://nodejs.org/en/)

[NPM JS Docs](https://docs.npmjs.com/)

[Express JS Docs](http://expressjs.com/en/4x/api.html)

[Superagent Docs](https://visionmedia.github.io/superagent/)

[Dotenv Docs](https://www.npmjs.com/package/dotenv)

[Google Geocoding API Docs](https://developers.google.com/maps/documentation/geocoding/start)

## Configuration

- `.env` - with your PORT and API keys. Make sure this file is in your `.gitignore` so your keys are not pushed to GitHub.
- `README.md` - with documentation regarding your lab and its current state of development. Check the "documentation" section below for more details on how that should look **AT MINIMUM**
- `.gitignore` - with standard NodeJS configurations
- `.eslintrc.json` - with Code 301 course standards for the linter
- `package.json` - with all dependencies and any associated details related to configuration
- Note that the `package-lock.json` file is automatically created when dependencies are installed and ensures that future installations of the project use the same versions of the dependencies.

```sh
lab-06-repository
   ├── .env
   ├── .eslintrc.json
   ├── .gitignore
   ├── package-lock.json
   ├── package.json
   └── server.js
```

## User Acceptance Tests

### Overview

In labs 6 through 9, you will be building a stand-alone back end which will interact with a static front end. Working with a new partner each day, you will request data from a total of six third-party APIs, modify the data as needed, and send the data to the client to be displayed in the browser. In labs 8 and 9, you will be persisting data in a SQL database.

Every day, you and your new partner(s) will deploy your back end as a new instance on Heroku.

You will have access to view the code base for the client, but will not be able to modify it in any way.

For this lab assignment, you will convert a location entered by the user into a latitude and longitude. As your City Explorer back end progresses in labs 6 through 9, you will use the latitude and longitude to request information from other APIs from the same search query.

### Repository set-up

- One person from your group should create a new repository on GitHub called `lab-06-back-end`. Add your partner(s) as collaborator(s).
- From this point on, work on semantically-named non-master branches. Once your app is functioning correctly on your branch, make a PR to master and confirm functionality on your deployed site. Your deployed site **should not** contain any broken functionality.

### Heroku deployoment

- One person from your group should create an instance on Heroku. Refer to lecture 5 for a reminder of the steps, if needed.
- From the Heroku dashboard, select your instance. In the Settings tab, click on the "Reveal Config Vars" button. Enter your API keys.
- In the Deploy tab, connect your instance to your repository and enable automatic deploys from your master branch. Deploy your application and make sure there are no errors. 

### Feature #1: Obtain latitude and longitude

#### Why are we implementing this feature?

- As a user, I want to enter the name of a location so that I do not need to look up the latitude and longitude every time I learn about a new location.

#### What are we going to implement?

Given that a user enters a valid location in the input  
When the user clicks the "Explore!" button  
Then the map will be populated with the location centered on the latitude and longitude of the search query  

#### How are we implementing it?

- Create a route with a method of `get` and a path of `/location`. The route callback should invoke a function to convert the search query to a latitude and longitude. The function should make a Superagent-proxied request to the Google Maps Geocoding API. 
- Return an object which contains the necessary information for correct client rendering. See the sample response, below.
- Confirm that your route is responding as expected by entering your deployed backend URL in the static client, then searching for a location.
- Redeploy your application.

Endpoint:
`/location`

Example Response:
```json
{
  "search_query": "seattle",
  "formatted_query": "Seattle, WA, USA",
  "latitude": "47.606210",
  "longitude": "-122.332071"
}
```

## Documentation

_Your `README.md` must include:_

```md
# Project Name

**Author**: Your Name Goes Here
**Version**: 1.0.0 (increment the patch/fix version number if you make more commits past your first submission)

## Overview
<!-- Provide a high level overview of what this application is and why you are building it, beyond the fact that it's an assignment for this class. (i.e. What's your problem domain?) -->

## Getting Started
<!-- What are the steps that a user must take in order to build this app on their own machine and get it running? -->

## Architecture
<!-- Provide a detailed description of the application design. What technologies (languages, libraries, etc) you're using, and any other relevant design information. -->

## Change Log
<!-- Use this area to document the iterative changes made to your application as each feature is successfully implemented. Use time stamps. Here's an examples:

01-01-2001 4:59pm - Application now has a fully-functional express server, with a GET route for the location resource.

## Credits and Collaborations
<!-- Give credit (and a link) to other people or resources that helped you build this application. -->
-->
```

## Submission Instructions

- Complete your Feature Tasks for the day
- Create a Pull Request (PR) back to the `master` branch of your repository
- On Canvas, submit a link to your PR and a link to your deployed application on Heroku. Add a comment in your Canvas assignment which includes the following:
  - A question within the context of today's lab assignment
  - An observation about the lab assignment, or related 'Ah-hah!' moment
  - How long you spent working on this assignment
