# project-manager
Project management tool for engineers and business people


### Server-side
```bash
# Make sure MongoDB is running (listening on port 21017, by default)
sudo service mongod start

# Then, run the server
yarn dev
```

### Client-side
```bash
# Start Vue
yarn serve
```



### Apollo GraphQL's Playground

#### Testing 'Email Capture'
This playground is used to test the API without worrying about the UI
```bash
# To open the playground, start by launching the server with this command
yarn dev

# Then, connect with your browser to 'http://localhost:5500/playground'
```

```javascript
// In order to send a request, we need to write a 'mutation' :
mutation CaptureEmail($email: String!) {
    captureEmail(email: $email) {
        id
        email
    }
}
```
```bash
# Then, got to the tab 'QUERY VARIABLES' and enter an email
{
    "email": "email@example.com"
}

# You should receive a confirmation of creation

# To confirm on Mongo, open a shell and type :
mongo
show dbs
use <your-db-name>
show collections
# You should see 'users'
db.users.find().pretty()
# You should see all the user entries in JSON format
```

#### Testing Signup
```javascript
// We start by writing a 'mutation'
mutation Signup ($id: String!, $firstname: String!, $lastname: String!, $password: String!){
  signup(id: $id, firstname: $firstname, lastname: $lastname, password: $password) {
    token
    user {
      id
      email
    }
  }
}
```

```bash
# Then, got to the tab 'QUERY VARIABLES' and enter user credentials
# N.B. We need to fetch the user's ID from Mongo
{
  "id": "5c2a0c02b07eac693157ba9e",
  "firstname": "John",
  "lastname": "Doe",
  "password": "mypassword"
}
```