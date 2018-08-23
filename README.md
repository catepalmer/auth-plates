# Manbook

<img src="https://i.kym-cdn.com/photos/images/original/001/345/499/0f6.jpg">


A Facebook wannabe in a shiny, manly new package. Sign up to be granted your new manly name and persona, connect with your bros, slide into your bros' DMs, see your posts and comments automatically translated into Manspeak so you don’t have to worry about coming across as sufficiently Alpha. The idea for this social media platform came from one sneering hipster's/incorrigible shit-stirrer’s/cynical feminist's fixation on a manly name generator available at http://www.rabbly.net/names/manlynames.html; the app’s creator in no way endorses toxic masculinity or its rancid effluvia.

## App name ideas
    * ManZone
    * Manbook
    * ManCave
    * BroZone
 
## User stories
## MVP

* As a user:
    - I would like to be able to register and log in/out
    - I would like to be assigned a name and profile picture/description when I register
    - I would like to be able to add other users as 'bros' and accept bro requests from other users
    - I would like to be able to chat in real time with my bros
    - I would like to be able to write posts that my bros can see in their newsfeeds
    - I would like to be able to view my own and other users' profiles
    - I would like to be able to view a newsfeed consisting of my own and my bros' posts
    - I would like to be able to comment on and like posts
    - I would like all posts/comments I make or direct messages I send to be automatically translated into Manspeak so I can feel more Alpha

## Stretch

* As a user:
    - I would like to able to post on my bros' walls
    - I would like to be able to edit my profile
    - I would like to take a quiz when I register so a profile is assigned to me based on the data I input
    - I would like to be able to delete posts and comments I've made as well as messages I've sent, because I sometimes say stupid shit online without thinking it through beforehand/I sometimes log in whilst drunk
    - I would like to be able to see fake ads on the side of my screen geared towards exploiting my insecurities and persuading me to buy shit I don't need, e.g. online pick-up artistry courses, power tools, whey protein powder, and gym memberships
    - I would like for some small percentage of the words/phrases in my posts, comments, and DMs to be translated into Manspeak in a way that gives them homoerotic undertones


## Views (client side)
  | name | purpose |
  | --- | --- |
  | Login | View for user to enter their login details |
  | Register | View for user to sign up for Manbook |
  | Home | View where user can see their newsfeed and a navigation bar |
  | Profile | View where user can see their own or another user's profile |
  | Bros | View where user can see a list (with profile pics) of all their or another user's bros |
  | ChatWindow | A window where user can chat with their bros |






From here, yet to be edited (taken from The Persistence EDA group project readme):

## Reducers (client side)

  | name | purpose |
  | --- | --- |
  | auth | Store information regarding user logins, auth status and auth errors |
  | game | Store info about game name, time started, host and whether finished or in progress |
  | users | store the list of players who can join games |

 ## Actions

 ### currentGame

 | type | data | purpose |
 | --- | --- | --- |
 | START_GAME | Players, inProgress | initialize game state |
  
 ### games
 
 | type | data | purpose |
 | --- | --- | --- |
 | RECEIVE_GAMES | games | retrieve list of games for the lobby |

 ### users
 | type | data | purpose |
 | --- | --- | --- |
 | RECEIVE_USERS | users | retreive the users from the server |
 

## API (Client - Server)

| Method | Endpoint | Protected | Usage | Response |
| --- | --- | --- | --- | --- |
| Post | /api/auth/login | Yes | Log In a User | The Users JWT Token |
| Post | /api/auth/register | Yes | Register a User | The Users JWT Token |
| Post | /api/game/new | Yes | Create a new game and populate with host | Game object |
| Post | /api/game/join | Yes | Add player to a game | The user id and game id |
| Post | /api/game/start | Yes | Begin a game | The game object |

## DB (Server Side)
  Game settings in seperate JSON file
  Theere should be three tables for MVP

### Users
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | user_name | String |
  | display_name | String |
  | img | text |
  | hash | text |

### Games
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | is_finished | Boolean |
  | in_progress | Boolean |
  | time_stamp | Integer |

### Missions
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | outcome | Boolean |
  | game_id | Integer |

  ### Rounds
  | Column Name | Data Type |
  | --- | --- |
  | id | Integer |
  | round_number | Integer |
  | mission_id | Integer |
  | leader_id | Integer |

  ### Intentions
  | Column Name | Data Type |
  | --- | --- |
  | intention | Boolean |
  | mission_id | Integer |
  | user_id | Integer |

  ### Votes (Join Table)

 Rounds have multiple votes
 
  | Column Name | Data Type |
  | --- | --- |
  | round_id | Integer |
  | vote | Boolean |
  | user_id | Integer |

  ### Nominations (Join Table)

 Rounds have multiple nominated players
 
  | Column Name | Data Type |
  | --- | --- |
  | round_id | Integer |
  | user_id | Integer |
  
  ### Players/Roles
  | Column Name | Data Type |
  | --- | --- |
  | game_id | Integer |
  | user_id | Integer |
  | role | String |

 ===========================================================================

### Players Chicken Tendies (Join Table M2M)

  Many Users play Many Games

 | Column Name | Data Type |
 | --- | --- |
 | user_id | Integer |
 | game_id | Integer |


<span id="anchor-7"></span>Setup
--------------------------------

Run the following commands in your terminal:

yarn install

yarn knex migrate:latest

yarn knex seed:run

mv .env\_example .env

To run in development:

yarn dev

 - or -

npm run dev

To run in production:

yarn start

 - or -

npm start

<span id="anchor-8"></span>Heroku!!!
------------------------------------

### <span id="anchor-9"></span>Creating your app

Create your app with **heroku create \[name\]**

You can check that this was successful by running **heroku apps** to view a list of your apps

### <span id="anchor-10"></span>Adding postgres

Add postgresql (hobby dev) to your app at **https://dashboard.heroku.com/apps/\[APP NAME HERE\]/resources**

Check that pg has been added by running **heroku addons** to ensure the postgresql db is on your app

### <span id="anchor-11"></span>Deploying!

I have created several npm scripts that will be useful for deploying your app to heroku easily.

To push your local master branch to your heroku app:
```sh
yarn h:deploy
  - or -
npm run h:deploy
```

Run heroku migrations:
```sh
yarn h:migrate
  - or -
npm run h:migrate
```

Run heroku seeds:
```sh
yarn h:seed
  - or -
npm run h:seed
```

If ever you need to rollback, you can also:
```sh
yarn h:rollback
  - or -
npm run h:rollback
```


### Ta-Da!
Your app should be deployed!
