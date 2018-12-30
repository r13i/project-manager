# project-manager
Project management tool for engineers and business people


### Server-side
```bash
# Make sure MongoDB is running (listening on port 21017, by default)
sudo service mongod start

# Then, run the server
yarn dev

# To test email adding to the DB, got to 'localhost:5500/playground' and write a 'mutation' :
```
```javascript
mutation CaptureEmail($email: String!) {
    captureEmail(email: $email) {
        id
        email
    }
}
```
```bash
# Then, got to 'QUERY VARIABLES' and enter an email
{
    "email": "email@example.com"
}

# You should see receive a confirmation of creation

# To confirm on Mongo, open a shell and type :
mongo
show dbs
use <your-db-name>
show collections
# You should see 'users'
db.users.find().pretty()
# You should see all the user entries in JSON format
```




### Client-side
```
# Start Vue
yarn serve
```