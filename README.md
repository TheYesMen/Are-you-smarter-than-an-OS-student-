# smarterThanOSStudent
Trivia app to play with your friends!

# Table of Contents
- Description
- Required Dependencies
- Installation and Start-up Guide
- - Server Setup
- - Google OAuth setup
- - AWS Deployment Setup
- - Schema example
- - Mongo Atlas Setup
- User Guide
- - Login/Account Creation
- - Updating User Profiles
- - Playing Trivia
- - Viewing the Leaderboard

# Description
smarterThanOSStudent is a trivia app that is designed to track your progress as you play through multiple rounds of trivia. The game is made in such a way that there are different game modes to select from and each player's stats are saved under their own account, created using their google credentials. There is a Daily game mode that allows all users to attempt the same trivia questions that are randomized every 24 hours. There is our classic game mode that allows users to attempt 5 general knowledge questions. Finally, there is a custom game mode that allows users to choose the contraints of their trivia game based on three dropdown fields.
On inital entry you're prompted to login using google OAuth, and if you're not a returning user a new account is created defaulting to your google display name as your username. Upon successful login authentication user is prompted to select a game mode.
Each player has a unique player profile that can be modified by clicking on their name in the navigation bar. They're able to upload a personal image and customize their username (as long as it does not match the username of any other active player in the database).

# Application 
Entertainment/Games

# Dependencies 
```
"dependencies": {
    "@emotion/react": "^11.9.0",
    "@emotion/styled": "^11.8.1",
    "@material-table/core": "^5.0.0-experimental.0",
    "@material-ui/core": "^4.12.4",
    "@mui/icons-material": "^5.8.0",
    "@mui/lab": "^5.0.0-alpha.83",
    "@mui/material": "^5.8.1",
    "@mui/styles": "^5.8.0",
    "axios": "^0.27.2",
    "cors": "^2.8.5",
    "dotenv": "^16.0.1",
    "dotenv-webpack": "^7.1.0",
    "express-session": "^1.17.3",
    "node-cron": "^3.0.0",
    "passport": "^0.6.0",
    "passport-google-oauth2": "^0.2.0",
    "react": "^18.1.0",
    "react-dom": "^18.1.0",
    "react-router-dom": "^6.3.0"
  },
  "devDependencies": {
    "@babel/core": "^7.18.0",
    "@babel/preset-env": "^7.18.0",
    "@babel/preset-react": "^7.17.12",
    "babel-loader": "^8.2.5",
    "css-loader": "^6.7.1",
    "eslint": "^8.15.0",
    "eslint-config-airbnb": "^19.0.4",
    "eslint-plugin-import": "^2.26.0",
    "eslint-plugin-jsx-a11y": "^6.5.1",
    "eslint-plugin-react": "^7.30.0",
    "eslint-plugin-react-hooks": "^4.5.0",
    "express": "^4.18.1",
    "file-loader": "^6.2.0",
    "html-webpack-plugin": "^5.5.0",
    "mongoose": "^6.3.4",
    "mongoose-findorcreate": "^3.0.0",
    "style-loader": "^3.3.1",
    "webpack": "^5.72.1",
    "webpack-cli": "^4.9.2"
  }
```
# Installation and Start-up
## Server/initial Setup
1. Fork TheYesMen/Are-you-smarter-than-an-OS-student- repo
2. Clone your forced repo to your local system
3. Run npm install to install dependancies
```
npm i
```
4. Create a .env file in your main directory. You can run the following command to create your .env file using .env.example as a base model.
```
cp .env.example .env
```
5. Compile your files to create bundle.
```
npm run build:client
```
6. Start the server
```
npm start
```

## Google OAuth
Google Oauth requires a google cloud account. First create your account and then navigate to the developer console. Go to credentials and press "create credentials" and then click "OAuth Client ID". Follow the on-screen promps until you've recieved a CLIENT_ID and CLIENT_SECRET. These values go inside the .env file. Also ensure you add all authorized redirect URI's to your google API credentials.

## AWS Deployment
An AWS EC2 instance was used to deploy the application. Some tips for deployment can be found in the deploy.md file included in this repo.

## Schema Model Example
The schema's for your DB are declared in the following path:
```
~/server/db/models
```

## Mongo Atlas Setup
We deployed using Mongo Atlas to manage our database. Navigate to Mongo Atlas' webpage and signup for their service. Create a cluster. From Mongo Atlas' Home screen you can select "Database" under the "Deployment" title in the left hand side of the navigation menu. On your cluster, click the "connect" button, then choose the "Connect your application" option on the following window. Here, you should see your DB's URI. Ensure that your .env ATLAS_URI points you to the appropriate database for your project.

# User Guide
## Login/Account Creation
When visiting for the first time users will have the ability to view the leaderboards, but in order to use any other functionality of the webpage you must create an account. Our account creation is handled through google and can be accessed through one of the many 'Login' buttons on the page. Most other buttons will also redirect you to a login page if you're not logged in.
1. Click login
2. After being redirected to google, enter your google credentials.
3. After being redirected back to smarterThanOSStudent, you'll be logged in.
4. If no account existed with that email, a new account will be created using your google display name as your username.

## Updating User Profiles
The user has the ability to change some of their profile information after creation. In order to do so, navigate to the user profile screen by clicking on your username/profile photo in the top navigation bar. On this screen users will have the option to change a few things:
1. Your profile photo. You can either upload a custom image or set your profile image to a default image by clicking the corresponding buttons. Images uploaded are stored on a cloudinary server.
2. Your username. Users are able to input any custom username into the field and so long as no other user exists in the database with the desired name, upon submit your username will be updating in the database and on the screen.
3. Account Deletion. If a user decides they no longer want their account to exist within our database they can delete it with the accoutn deletion button. This button will prompt you to input a check to ensure you are sure you want to delete your account and all stats associated with it.

## Playing Trivia
Users can decide between three game modes: Daily, Classic, and Custom.
1. Daily can only be attempted once daily. Upon visiting the daily questions page you will no longer have access to it for 24 hours.
2. Classic mode will always display 5 general knowledge multiple choice questions for the user to attempt.
3. Custom mode allows users to choose the catagory, number of questions (in increments of 5) and difficulty of the questions.
4. Every question attempted in immediatly added to your stats. Users only recieve a win if all questions displayed are answered correctly.

## Viewing the Leaderboard
The leaderboard will show the current stats of all users in the database. It can be displayed by checking the top 5 from the home screen, or from the Leaderboard page on the navigation bar. When viewing the leaderboard it can be sorted and filtered by any individual column (wins/Qs answered, etc). If your current questions correct is higher than 90% than a 🔥 emoji will be displayed next to your user on the leaderboard.