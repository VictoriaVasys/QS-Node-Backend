# Quantified Self Backend
#### This app is built with Node.js & Express.js; it provides an API to be used with the Quantified Self Frontend.
The live app is found here: https://ms-vv-quantified-self.herokuapp.com/
The front-end that the app serves is found here: https://victoriavasys.github.io/QS-Frontend/

## Node/Express Development Setup
1. Clone this repo
2. Navigate to the root directory
3. Install dependences `npm install` or `npm i`
4. Create databases
```
psql
CREATE DATABASE qs
CREATE DATABASE qs_test
```
5. Build the database
```
knex migrate:latest
knex migrate:latest --env test
```
6. Seed the database `knex seed:run`
7. Start the server `npm start`

## Mocha/Chai Testing
* Run tests with `npm test`
* Run all tests with `npm test test/*`
* Specify a test with `npm test test/<test-name>.js`

## Object-relational map
![Object relational map image](/../screenshots/screenshots/orm-schema.png?raw=true "Object Relational Map Image")

## API Endpoints
#### All endpoints are RESTful and all responses are in JSON format. Some important things to note:

* All API endpoints begin with `https://quantified-self-vv-ms.herokuapp.com/api/v1/`
* Requests are case sensitive
* Params for POST and PUT requests should be passed as x-www-form-urlencoded  **<-- what does this mean?**

### Foods
|**HTTP Verb/Method**|**URI Path**|**Description**|**Parameters**|
| --- | --- |:---:| --- |
|GET|foods|returns an array of all active foods|none|
|GET|foods/:id|returns a food based on `id`|none|
|POST|foods|adds an active food to the database|`?name=<string>&calories=<integer>`|
|PUT|foods/:id|updates a food|`?name=<string>` or `?calories=<integer>`|
|DELETE|foods/:id|renders a food inactive|`?name=<string>` or `?calories=<integer>`| **is this restful?**

### Meals (Breakfast, Lunch, Dinner, Snacks)
|**HTTP Verb/Method**|**URI Path**|**Description**|**Parameters**|
| --- | --- |:---:| --- |
|GET|meals|returns an array of all meals|none|
|GET|meals/:id|returns a meal based on `id`|none|
|POST|mealFoods|adds a food to a meal|`?mealId=<integer>&foodId=<integer>`|
|DELETE|mealFoods/:id|removes a food from a meal|`?mealId=<integer>&foodId=<integer>`|


