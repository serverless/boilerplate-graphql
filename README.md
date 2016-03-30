# Serverless Boilerplate
[![serverless](http://public.serverless.com/badges/v3.svg)](http://www.serverless.com)

The goal here is not just to create the ultimate boilerplate project for building serverless applications, but to create an application boilerplate with the *lowest total cost of ownership* (e.g., the least code, administration, cost) by leveraging new tech (e.g., Lambda, GraphQL).

- [Setup](#setup)
- [Team](#team)

---

## Setup

### Serverless
If you haven't yet installed `serverless` on your machine, run `npm install -g serverless`. Then:

```
git clone https://github.com/serverless/serverless-boilerplate.git
cd serverless-boilerplate
serverless project init
```

After following the setup instructions, add the `authTokenSecret` variable to `_meta/variables/s-variables-STAGE-REGION.json` and give it a strong value. This is the secret used to hash passwords and generate JSON web tokens. Then:

```
cd back/api
npm install
serverless dash deploy
```

### Client
Set `API_URL` in `client/src/app/js/actions/index.js`

```
cd ../../client/src
npm install
npm start
```

### Testing With GraphiQL

You may use the [serverless-client-s3](https://github.com/serverless/serverless-client-s3) plugin to deploy a web client to S3.
 
- Set `API_URL` in `/client/dist/index.html`
- Run `serverless client deploy`

Alternatively (if you're running OSX), you can use the [GraphiQL Electron App](https://github.com/skevy/graphiql-app) to test the GraphQL backend without a client:

- Install [brew cask](https://caskroom.github.io) for easy installation: `brew tap caskroom/cask`
- Install GraphiQL App: `brew cask install graphiql`
- Open GraphiQL application. Just search for `GraphiQL` using OSX Spotlight Search!
- Add your data endpoint to the "GraphQL Endpoint" text field, and make sure the "Method" is set to `POST`.

Using your GraphiQL client, 

- Try this mutation to create the first user:


```
mutation createUserTest {
  createUser (username: "serverless", name: "Serverless Inc.", email: "hello@serverless.com", password: "secret") {
    id 
    username 
    name 
    email  
  }
}
```

- Now list all users using the following query:


```
query getUsersTest { 
  users {
    id
    username
    name
    email
  } 
}
```

- You should get the user you just created:


```
{
  "data": {
    "users": [
      {
        "id": "aca42ee0-f509-11e5-bc11-0d8b1f79b4b9",
        "username": "serverless",
        "name": "Serverless Inc.",
        "email": "hello@serverless.com"
      }
    ]
  }
}
```

---

## Team
* [@eahefnawy](https://github.com/eahefnawy)
* [@minibikini](https://github.com/minibikini)
* [@ac360](https://github.com/ac360)
* [@kevinold](https://github.com/kevinold)
* [@pmuens](https://github.com/pmuens)
* [@erikerikson](https://github.com/erikerikson)
* [@ryansb](https://github.com/ryansb)
