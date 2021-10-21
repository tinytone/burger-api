# Burger-api

This is a repository containing a burger-api hosted using node

This inspiration for this project is from Ania Kobow's youtube video:

[Make your own mock API (super simple)](https://www.youtube.com/watch?v=FLnxgSZ0DG4)

Her github repo for the video is [here](https://github.com/kubowania/burger-api).

Ania then deployed her Burger API to Heroku, so the live version of her API can be found here: 
https://my-burger-api.herokuapp.com/burgers

# Steps in Video

## Create a new repo on github

- Click the new button on your github repo: https://github.com/new
- Enter a Repository name e.g. **burger-api**
- Make it public
- Add a README.MD file
- Add a .gitignore file selecting the **node** from the dropdown

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

> The burder data for the new json file was copy and pasted from Ania's [db.json](https://github.com/kubowania/burger-api/blob/main/db.json) on her github repo.

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



# Ania's Notes:


>My Burger Api
>
>Hello everyone! In this weeks video I show you how to make your own mock version of an API and deploy it onto the internet in just a few easy steps. This is a super stripped down version, so has no routing/controllers. This is thanks to the https://github.com/typicode/json-server​ package. Where you can get a mock REST API with zero coding in less than 30 seconds.
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