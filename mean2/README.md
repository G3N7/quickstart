# MEAN2 Stack (MongoDB, Express, Angular2, Node.js)

## Installation (_Windows_)
* Install _Node.js_
* Install _Visual Studio Code_
* Install _Angular Cli_ (a great tool for building Angular 2+ applications)

### Install _Node.js_
Install the [LTS from the Node website](https://nodejs.org/en/).

In a console (I would suggest [_cmder_](http://cmder.net/) for _Windows_) type ` npm --version` to verify you get a version number back, for example `3.10.10`

You now have node on your machine.

### Install _Visual Studio Code_
Install [_Visual Studio Code_](https://code.visualstudio.com/Download).  This is a lightwieght, cross-platform IDE with great support for what we are doing.

### Install _Angular Cli_
In a console (I would suggest [_cmder_](http://cmder.net/) for _Windows_) types `npm install -g @angular/cli`

### Install _MongoDB_
TODO:DESCRIPTION

## Project Setup

### Meta Setup
Create a simple folder structure.
```batch
mkdir "your-project"
cd "your-project"
mkdir "api"
mkdir "app"
```

Setup git, since this will help us save our changes at each step:
```batch
git init
```

Put a copy of the [.gitignore](https://github.com/github/gitignore/blob/master/Node.gitignore) that the community uses into the root of our project.

We also want to go ahead and start our mongo, so in a new console instance, go ahead and navigate to where your mongod.exe is, or set it in the `PATH` variable, and go ahead and invoke mongod.exe to start mongo.

### API Setup
Setup a basic shll for our api, this will put the piping in place for rapid development.

#### Initialize Node
```batch
cd "api"
npm init -y
npm install nodemon npm-run-all rimraf typescript --save-dev
```
Feel free to edit things like description, in the project.json itself.

#### Setup Typescript
Add our [tsconfig.json](TODO:SAMPLE), this will control the typescript compiler.
```typescript
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "outDir": "dist"
  },
  "include": [
    "src/**/*.ts"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

#### Install API Framework Packages
We will install some dependencies that will help us "express" our api or backend.
```batch
npm install --save express cors mongoose body-parser
npm install --save-dev @types/express @types/cors @types/mongoose @types/body-parser
```

#### Create our entry point
Create a file `api/src/api-entrypoint.ts` and add the following parts.

First lets import our dependencies.
```typescript
import * as express from 'express';
import * as path from 'path';
import * as bodyParser from 'body-parser';
import * as cors from 'cors';
import * as mongoose from 'mongoose';
```

Next lets create our app and database connection.
```typescript
//Initialize our app variable
const app = express();

//Declaring Port
const port = 3000;

// Connect mongoose to our database
mongoose.connect(`mongodb://localhost:27017/`);
```

Then we will configure some of middleware that helps make things easier
```typescript
//Middleware for CORS
app.use(cors());

//Middleware for bodyparsing using both json and urlencoding
app.use(bodyParser.urlencoded({extended:true}));
app.use(bodyParser.json());
```

Then we will setup a basic route to demonstrate how
```typescript
app.get('/', (req,res) => {
    res.send("Invalid page");
});

//Listen to port 3000
app.listen(port, () => {
    console.log(`Starting the server at port ${port}`);
});
```

#### Setup our Build/Server
Add our scripts to the [package.json](TODO:SAMPLE), these will allow us to make changes and see them reflected immediately.
```typescript
{
  /* more config */
  "scripts": {
    "clean": "rimraf dist",
    "start": "npm-run-all clean build --parallel watch:build watch:server --print-label",
    "build": "tsc",
    "watch:build": "tsc --watch",
    "watch:server": "nodemon dist/api-entrypoint.js --watch ."
  }
  /* more config */
}
```

We can see that `npm start` will kick off a chain of actions, first `clean` our output directory, then `build` once to start our loop, then in parallel `watch:build` and `watch:server`

Now lets go ahead and give the app a shot, lets type `npm start` from the `api` directory.

Try browsing to http://localhost:3000

### App Setup
We will now setup our angular app.  In a console, navigate back up to the root source directory.  Now we will use _angular-cli_ to initialize our frontend.
```batch
ng new my-awesome-app --style=scss --directory app --prefix ma --routing --skip-git
```
Lets break this command down a bit.

* `ng new` lets us create a new angular app.
* `my-awesome-app` lets us set the name of the frontend app.
* `--style=scss` sets our preference to scss for app/component styles
* `--directory app` says to fill it into our a subdirectory called app.
* `--prefix ma` this lets us set the prefix that we will use for our components, for example `<ma-user-detail></ma-user-detail>`
* `--routing` tells angular to go ahead and setup/maintain a routing module for us.
* `--skip-git` since we already have a higher level git directory.

Navigate to `app` and then `ng serve`.