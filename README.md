<br />
    <p>
    <a href="https://www.npmjs.com/package/aoi.fb"><img src="https://cdn.discordapp.com/attachments/929747405916733460/934447223117340732/AoiFB_LogoTransparent_2.0.png" alt="aoi.fb" /></a>
  </p>

# aoi.fb

A Firebase database of wrapper using aoi.fb as API


## Table Of Contents

- [About](#about)
- [Installation](#installation)
  - [Setup](#setup)
- [Methods](#methods)
  - [SET](#set)
  - [GET](#get)
  - [ALL](#all)
  - [DEL](#del)
- [Others](#others)
  - [PING](#ping)
- [Aoi.FB](#aoi.fb)
- [Open Source](#open-source)

## About
A Firebase database of wrapper using aoi.fb as API
[![NPM Version](https://img.shields.io/npm/v/aoi.fb.svg?maxAge=3600)](https://www.npmjs.com/package/aoi.fb)
[![NPM Downloads](https://img.shields.io/npm/dt/aoi.fb.svg?maxAge=3600)](https://www.npmjs.com/package/aoi.fb)
## Installation

**Node.JS 16.0.0 or newer is required.**  

```sh-session
npm install aoi.fb@latest
```

### Setup

**Create a file in the root folder of your project (in the same folder where your index is) with the name:** `att.sh`
**Then add the code below into the file:**
```sh-session
rm ./node_modules/aoi.js/src/classes/*
cp ./node_modules/aoi.fb/src/adjust/* ./node_modules/aoi.js/src/classes/
```
**Then, in your index file, configure aoi.fb:**
```js
const aoifb = require("aoi.fb")

const firebase = aoifb.Create({
  apiKey: "",
  authDomain: "",
  databaseURL: "",
  projectId: "",
  storageBucket: "",
  messagingSenderId: "",
  appId: "",
  measurementId: ""
})

const aoijs = require("aoi.js")

const bot = new aoijs.Bot({
  token: "TOKEN", // Discord Bot Token
  prefix: "PREFIX",// Discord Bot Prefix
  intents: ["GUILDS", "GUILD_MESSAGES"], //Discord Bot Intents
  database: {
    type: "aoi.fb",
    db: firebase
  } // Change database to aoi.fb
})

// Event
bot.onMessage()

// Command Example for Database Latency
bot.command({
  name: "ping",
  code: `Pong!
> Bot Latency: $pingms
> Database Latency: $djsEval[client.db.db.ping();yes]`
})

bot.readyCommand({
  channel: "",
  code: `$log[Ready on $userTag[$clientID]]`
})

```

## Methods
### SET
#### Description - To set a value to a referenced key
#### Example - 
```js
client.db.db.set('table', 'key', 'value')
```
### GET
#### Description - To get the value of a reference
#### Example - 
```js
client.db.db.get('table', 'key')
```

### ALL
#### Description - Returns all values of the reference
#### Example - 
```js
client.db.db.all('table').then(a => a.map(b => b.key))
```
### DEL
#### Description - To delete all the values made in the reference, be it the whole table, or a directory further down
#### Example - 
```js
client.db.db.delete('table') or client.db.db.del('table', 'key')
```

## Others
### PING
#### Description  - Returning to Database Latency
#### Example - 
```js
client.db.db.ping()
```

## Aoi.FB

aoi.fb, a Firebase database of wrapper using aoi.fb as API

Owned by [GR](https://github.com/guihrib/) </br>

## Open Source

aoi.fb is a package and db made for developers using aoi.js. Also made by you! If you want to contribute just do a [pull-request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)