#DarkLord
Stateless Authentication Server - JWT based authentication

##Technology:

- [NodeJS](http://nodejs.org/)
- [PassportJS](http://passportjs.org/)
- [MongoDB](http://www.mongodb.org/)
- [Mongoose](http://mongoosejs.com/)
- [JWT Simple](https://www.npmjs.org/package/jwt-simple)

## API

### POST /token
Generate an authentication token.

**Request:**

    {
      "email": "myemail@address.com",
      "password": "123456"
    }

**Response:**

    {
      "token": "<authentication-token>",
      "refresh": "<short-term-refresh-date>",
      "expires": "<long-term-expiry-date>"
    }

### POST /register
Create an account and generate an authentication token.

**Request:**

    {
      "email": "myemail@address.com",
      "password": "123456"
    }

**Response:**

    {
      "token": "<authentication-token>",
      "refresh": "<short-term-refresh-date>",
      "expires": "<long-term-expiry-date>"
    }

### PUT /change
Change the password on the account. 

**Request:**

    {
      "email": "myemail@address.com",
      "password": "abcdef"
    }
		Headers:
		Authorization: "<authentication-token>"

### POST /forgot
Creates a forgot password token and emails the user the link to reset.

**Request:**

    {
      "email": "myemail@address.com"
    }

### POST /reset
Accepts a token and a password, the server then update the account password

**Request:**

    {
      "token": "<forgotten-password-token>",
      "password": "654321"
    }
