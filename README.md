### Marvelous validation for JS / NodeJS

#### installation

```
npm install --save @validify-js/core
```

---

**please, buy me a coffe to support this package**.

## [![buy me a coffee](https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg)](https://www.buymeacoffee.com/faridmansimli)

---

### Table of contents

1. [Creating Schema](#schema)
2. [validating an object](#validating)
3. [Using with NodeJS](#nodejs)

#### an example of how to create a valid schema to validate an object: <a name="schema"></a>

```
import { Schema } from "@validify-js/core";

const userSchema = new Schema({
  name: { required: false, minLength: 5 },
  email: {
    required: true,
    email: true,
    message: "email is required!"  // if you omit message field default message will be displayed
  },
  password: {
    required: true,
    pattern: /[A-Za-z0-9]{8,}/g
  },
  age: {
    required: false,
    min: 18,
    max: 30
  },
});

```

**you can validate any object by using the schema wich we created above. for example:** <a name="validating"></a>

```
const user = {
  name: "Farid",
  surname: "Mansimli",
  email: "farid@example.com"
};

const { ok, data, errors } = userSchema.validate(user);

// validation will be failed. (ok --> false),
// because "password" field is required in the above schema.


```

## how to use it with NodeJS ? that's amazingly easy <a name="nodejs"></a>

```
// best practice! create the schema as a seperate file and import it to keep code clean.

import { Schema } from "@validify-js/core";

const loginSchema = new Schema({
  username: {
    required: true,
    minLength: 5,
    maxLength: 15,
    message: "username is required!"
  },
  password: {
    required: true,
    pattern: /[A-Za-z0-9]{8,}/g
  }
});

// Express.js route handler

const loginHandler = (req, res, next) => {

  const { ok, data, errors} = loginSchema.validate(req.body);

  // "ok" means req.body is valid , you are good to go!
  // "data" includes property values
  // "errors" includes the error messages of invalid fields , if exists


  try {

    if(!ok){
      throw new Error("validation failed");
      error.errors = errors;
    }

    // do some stuff, and return response.

  } catch (error) {
    next(error);
  }

}

```

you might not belive, however, that's pretty much it, as simple as you see

**that's pretty much it, guys!**

---

**you can reach me here:**

[**Linkedin**](https://linkedin.com/in/faridmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Facebook**](https://facebook.com/fmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Twitter**](https://twitter.com/faridmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Instagram**](https://instagram.com/faridmansimli)

---

**please, buy me a coffe to support this package**.

## [![buy me a coffee](https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg)](https://www.buymeacoffee.com/faridmansimli)

---
