# Burger-api

This is a repository containing a burger-api hosted using an npm package called [json-server](https://github.com/typicode/json-server).

The contents our of repo were then pushed to Heroku and the Burger API put live. This API can be viewed at the following URL: https://tinytones-burger-api.herokuapp.com/

## Credit

This inspiration for this project is from Ania Kobow's youtube video:

[Make your own mock API (super simple)](https://www.youtube.com/watch?v=FLnxgSZ0DG4)

Her github repo for the video is [here](https://github.com/kubowania/burger-api).

Ania then deployed her Burger API to Heroku, so the live version of her API can be found here: 
https://my-burger-api.herokuapp.com/burgers

# Files

The following files are in the repository:

| File name| Description |
|----------|-------------|
| [.gitignore](https://github.com/tinytone/burger-api/blob/master/.gitignore) | Lists the files and folders to ignore when adding/committing via git. We want to ignore the ```node_modules``` folder. |
| [db.json](https://github.com/tinytone/burger-api/blob/master/db.json) | This contains our burger data in json format. |
| [package.json](https://github.com/tinytone/burger-api/blob/master/package.json) | Lists our dependencies as well as start shortcut command. |
| [package-lock.json](https://github.com/tinytone/burger-api/blob/master/package-lock.json) | Locks our npm packages at a specific version for other developers using this source code. |
| [server.js](https://github.com/tinytone/burger-api/blob/master/server.js) | A start script, hotkeyed to "npm start" which enables us to start the json-server package pointing it at our db.json file. This essentially creates a host which listens on a localhost port of 3000, allowing us to interact with our burger data using REST and the GET, POST, PUT, DELETE verbs. |
| README.md | Documentation about this repository |

# Steps in Video

## Create a new repo on github

- Click the new button on your github repo: https://github.com/new
- Enter a Repository name e.g. **burger-api**.
- Make it public.
- Add a README.MD file.
- Add a .gitignore file selecting the **node** option from the dropdown.

## Cloning the Repo

- On your local machine, open up a new powershell window in your "source code" folder
- Clone the repo to your local machine using git:

```powershell
PS C:\SourceCode\GitHub> git clone https://github.com/tinytone/burger-api.git

Cloning into 'burger-api'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (4/4), done.
```

## Opening the Code

Open up the Code in Visual Code by using:

```powershell
PS C:\SourceCode\GitHub> code .
```

## Creating the Database

Create a file called **db.json** in your project.

> The burger data for the new json file was copy and pasted from Ania's [db.json](https://github.com/kubowania/burger-api/blob/main/db.json) on her github repo.

```json
{
    "burgers": [
      {
        "id": 0,
        "name": "Tribute Burger",
        "restaurant": "Honest Burgers",
        "web": "www.honestburgers.co.uk",
        "description": "A mouth-watering honest beef burger",
        "ingredients": [
          "beef",
          "american cheese",
          "burger sauce",
          "french mustard",
          "pickes",
          "onion",
          "lettuce"
        ],
        "addresses": [
          {
            "addressId": 0,
            "number": "75",
            "line1": "Venn Street",
            "line2": "Clapham",
            "postcode": "SW4 0BD",
            "country": "United Kingdom"
          }
        ]
      },
      { 
          // etc
      }
    ]
}
```

## Installing NPM Packages

Ensure that you have both **node.js** and **npm** installed. Node.js can be downloaded from [here](https://nodejs.org/en/) which will also install npm.

Verifying versions:

```powershell
PS C:\SourceCode\GitHub\burger-api> node -v
v14.17.5

PS C:\SourceCode\GitHub\burger-api> npm -v
6.14.14
```

Using ```npm```, download and install the ```json-server``` package as follows

```
npm install -g json-server
```

E.g.

```
PS C:\SourceCode\GitHub\burger-api> npm install -g json-server
C:\Users\{your user}\AppData\Roaming\npm\json-server -> C:\Users\{your user}\AppData\Roaming\npm\node_modules\json-server\lib\cli\bin.js
+ json-server@0.17.0
added 173 packages from 80 contributors in 9.275s
```
## Starting the Json Server using json-server


Start the json server, pointing it at our burger database json file, as follows:

```
json-server --watch db.json
```

E.g.

```powershell
PS C:\SourceCode\GitHub\burger-api> json-server --watch db.json

  \{^_^}/ hi!

  Loading db.json
  Done

  Resources
  http://localhost:3000/burgers

  Home
  http://localhost:3000

  Type s + enter at any time to create a snapshot of the database
  Watching...
```

We can now browse to http://localhost:3000/burgers to view all burgers or http://localhost:3000/burgers/1 to view specific burgers!

At this point we're done! We've created an api reading a database with 2 commands! 
- npm install -g json-server
- json-server --watch db.json

Note:

The [db.json](https://github.com/tinytone/burger-api/blob/master/db.json) file has a burgers top level node. This is the "root" URL that json-server uses. Additional routes can be added by further modifying this json file:

```
{
    "burgers": []
} 
```

## Initialising our project

Time to initialise our project using 

```
npm init
```

This will ask you a series of questions which will then be added to a newly created [package.json](https://github.com/tinytone/burger-api/blob/master/package.json) file:

```powershell
PS C:\SourceCode\GitHub\burger-api> npm init

This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (burger-api)
version: (1.0.0)
description: A burger API hosted via json-server.
entry point: (index.js)
test command:
git repository: (https://github.com/tinytone/burger-api.git)
keywords: burger-api, json database, npm, node, json-server, heroku
author: Tony Harding (credit to Ania Kubow)
license: (ISC)
About to write to C:\SourceCode\GitHub\burger-api\package.json:

{
  "name": "burger-api",
  "version": "1.0.0",
  "description": "A burger API hosted via json-server.",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/tinytone/burger-api.git"
  },
  "keywords": [
    "burger-api",
    "json",
    "database",
    "npm",
    "node",
    "json-server",
    "heroku"
  ],
  "author": "Tony Harding (credit to Ania Kubow)",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/tinytone/burger-api/issues"
  },
  "homepage": "https://github.com/tinytone/burger-api#readme"
}

Is this OK? (yes) yes
PS C:\SourceCode\GitHub\burger-api>
```

Add a ```package-lock.json``` file by typing:

```
npm i
```

E.g.

```powershell
PS C:\SourceCode\GitHub\burger-api> npm i

npm notice created a lockfile as package-lock.json. You should commit this file.
up to date in 0.375s
found 0 vulnerabilities

PS C:\SourceCode\GitHub\burger-api>
```

Our [package.json](https://github.com/tinytone/burger-api/blob/master/package.json) file doesn't contain details about the json-server package that we initially installed, so lets run the command again to ensure that it's correctly added to the [package.json](https://github.com/tinytone/burger-api/blob/master/package.json) file:

```powershell
PS C:\SourceCode\GitHub\burger-api> npm i json-server
+ json-server@0.17.0
added 173 packages from 80 contributors and audited 173 packages in 6.807s

13 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

PS C:\SourceCode\GitHub\burger-api>
```

This has now updated this file and added in the dependencies data:

```json
{
  ...
  "homepage": "https://github.com/tinytone/burger-api#readme",
  "dependencies": {
    "json-server": "^0.17.0"
  }
}
```

## Adding a start script

Edit the [package.json](https://github.com/tinytone/burger-api/blob/master/package.json) file and add a "start" script, which starts the server.js file using node, as follows:

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server.js"
  },
```

## Creating a server javascript file

Create a new [server.js]((https://github.com/tinytone/burger-api/blob/master/server.js)) file with the following contents:

```js
const jsonServer = require('json-server');
const server = jsonServer.create();
const router = jsonServer.router('db.json');
const middlewares = jsonServer.defaults();
const port = process.env.PORT || 3000;

server.use(middlewares);
server.use(router);

server.listen(port);
```

Using our new start script, run the server using ```npm start```

E.g

```powershell
PS C:\SourceCode\GitHub\burger-api> npm start

> burger-api@1.0.0 start C:\SourceCode\GitHub\burger-api
> node server.js

GET /db 200 2.045 ms - -
GET /__rules 404 2.438 ms - 2
GET /burgers 304 25.011 ms - -
```

You can now browse to the server at the following URL: http://localhost:3000/

You can also browse to burgers at: http://localhost:3000/burgers

# Heroku:

> [Heroku](https://www.heroku.com/) is a platform as a service (PaaS) that enables developers to build, run, and operate applications entirely in the cloud, supporting several programming languages.
>
>One of the first cloud platforms, Heroku has been in development since June 2007, when it supported only the Ruby programming language, but now supports Java, Node.js, Scala, Clojure, Python, PHP, and Go.

## Registration / Signin

Register and create a new account with Heroku and then sign in.

You should be taken to your dashboard once logged in:

https://dashboard.heroku.com/apps

## Installing Heroku Locally

Ania uses the following command to install Heroku on her MAC:

```
brew tap heroku/brew && brew install heroku
```

This won't work on windows.

I'll be using npm:

```
npm install -g heroku
```

Verify the version of heroku installed:

```powershell
PS C:\SourceCode\GitHub\burger-api> heroku --version
heroku/7.59.0 win32-x64 node-v14.17.5
```

## Create a heroku project

Login to heroku via the CLI:

```powershell
PS C:\SourceCode\GitHub\burger-api> heroku login

heroku: Press any key to open up the browser to login or q to exit:
Opening browser to https://cli-auth.heroku.com/auth/cli/browser/{some-guid}}?requestor={some-requestor-data}
Logging in... done
Logged in as {my-email-address}
```

Now create a project within heroku using the CLI as follows:

```
PS C:\SourceCode\GitHub\burger-api> heroku create tinytones-burger-api

Creating ??? tinytones-burger-api... done
https://tinytones-burger-api.herokuapp.com/ | https://git.heroku.com/tinytones-burger-api.git
PS C:\SourceCode\GitHub\burger-api>
```

## Deploying to Heroku

Push our code to Heroku as follows:

```powershell
PS C:\SourceCode\GitHub\burger-api> git push heroku master

Enumerating objects: 14, done.
Counting objects: 100% (14/14), done.
Delta compression using up to 8 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (14/14), 26.40 KiB | 5.28 MiB/s, done.
Total 14 (delta 1), reused 4 (delta 0), pack-reused 0
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> Building on the Heroku-20 stack
remote: -----> Determining which buildpack to use for this app
remote: -----> Node.js app detected
remote:
remote: -----> Creating runtime environment
remote:
remote:        NPM_CONFIG_LOGLEVEL=error
remote:        NODE_VERBOSE=false
remote:        NODE_ENV=production
remote:        NODE_MODULES_CACHE=true
remote:
remote: -----> Installing binaries
remote:        engines.node (package.json):  unspecified
remote:        engines.npm (package.json):   unspecified (use default)
remote:
remote:        Resolving node version 14.x...
remote:        Downloading and installing node 14.18.1...
remote:        Using default npm version: 6.14.15
remote:
remote: -----> Installing dependencies
remote:        Installing node modules
remote:        added 173 packages in 3.075s
remote:
remote: -----> Build
remote:
remote: -----> Caching build
remote:        - node_modules
remote:
remote: -----> Pruning devDependencies
remote:        audited 173 packages in 1.671s
remote:
remote:        13 packages are looking for funding
remote:          run `npm fund` for details
remote:
remote:        found 0 vulnerabilities
remote:
remote:
remote: -----> Build succeeded!
remote: -----> Discovering process types
remote:        Procfile declares types     -> (none)
remote:        Default types for buildpack -> web
remote:
remote: -----> Compressing...
remote:        Done: 34.2M
remote: -----> Launching...
remote:        Released v3
remote:        https://tinytones-burger-api.herokuapp.com/ deployed to Heroku
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/tinytones-burger-api.git
 * [new branch]      master -> master

PS C:\SourceCode\GitHub\burger-api>
```

## Testing our newly deployed API

```
heroku open
```

This opens up a browser at the following URL: https://tinytones-burger-api.herokuapp.com/

We can now browse to and view our API at various URL's:
- https://tinytones-burger-api.herokuapp.com/burgers
- https://tinytones-burger-api.herokuapp.com/burgers/2
- https://tinytones-burger-api.herokuapp.com/burgers/4
- etc

Our [Heroku dashboard](https://dashboard.heroku.com/apps) also shows 1 newly deployed application:

https://dashboard.heroku.com/apps/tinytones-burger-api



# Ania's Notes:


>My Burger Api
>
>Hello everyone! In this weeks video I show you how to make your own mock version of an API and deploy it onto the internet in just a few easy steps. This is a super stripped down version, so has no routing/controllers. This is thanks to the https://github.com/typicode/json-server??? package. Where you can get a mock REST API with zero coding in less than 30 seconds.
>
>For those of you wishing to check it out live visit here
>
>A lot of you are wondering if you can interact with this database. Yes you can. You can make GET, POST, PUT, DELETE etc requests to it. You can even get an individual burger. For example if I want to get the Tribute Burger, which has an ID of 0, I would write:
>

```
fetch('https://my-burger-api.herokuapp.com/burgers/0')
  .then(response => response.json())
  .then(data => console.log(data));
```

>For those of you who would like to add a burger to my database, >please make a pull request here, following the same format as >discussed on this video.
>
>If you did like the video tutorial, please hit the Like and >Subscribe button so I know to make more!
>
>Twitter: https://twitter.com/ania_kubow<br>
>YouTube: https://youtube.com/aniakubow<br>
>Instagram: https://instagram.com/aniakubow<br>
>
>#burgerAPI