<br/>

# @validify-js/core &nbsp; =>> for JS / NodeJS

[![npm version](https://img.shields.io/npm/v/@validify-js/core)](https://www.npmjs.com/package/@validify-js/core) &nbsp; [![npm downloads/month](https://img.shields.io/npm/dm/@validify-js/core)](https://www.npmjs.com/package/@validify-js/core) &nbsp; [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/fmansimli/validify-js-core/blob/master/LICENSE)

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

```ts
// keep in mind that "type" property must be specified!!!
// for example type:Number

import { Schema } from "@validify-js/core";

export const user = new Schema({
  name: { type: String, required: false, minLength: 7 },
  email: { type: String, required: true, email: true },
  gender: { type: String, required: true },
  hobbies: {
    type: Array,
    required: true,
    minLength: 3,
    message: "3 hobbies should be selected at least!", // if you omit  the "message" field, default message will be displayed
  },
  blocked: {
    type: Boolean,
    required: false,
  },
  password: {
    type: Number,
    required: true,
    pattern: /[A-Za-z0-9]{8,}/,
  },
  age: {
    type: Number,
    required: false,
    min: 18,
    max: 30,
  },
  profession: {
    type: String,
    required: true,
  },
});
```

#### **you can validate any object by using the schema wich we created above. for example:** <a name="validating"></a>

```ts
const user = {
  name: "Farid",
  email: "farid@example.com",
  hobbies: ["sky-diving", "soccer"],
  age: 25,
};

const { ok, data, errors } = userSchema.validate(user);

// validation will be failed. (ok --> false),
// because, a few fields are required in the above schema.
```

## how to use it with NodeJS ? that's amazingly easy <a name="nodejs"></a>

```ts
// best practice! create the schema as a seperate file
// and import it to keep code clean.

import { Schema } from "@validify-js/core";

const loginSchema = new Schema({
  username: {
    type: String,
    required: true,
    minLength: 5,
    maxLength: 15,
    message: "username is required!",
  },
  password: {
    type: String,
    required: true,
    pattern: /[A-Za-z0-9]{8,}/,
  },
});

// Express.js route handler

const loginHandler = (req, res, next) => {
  const { ok, data, errors } = loginSchema.validate(req.body);

  // if "ok" is true, it means req.body is valid , you are good to go!
  // "data" includes property values
  // "errors" includes the error messages of invalid fields, if exists

  try {
    if (!ok) {
      throw new Error("validation failed");
      error.errors = errors;
    }

    // do some stuff, and return response.
  } catch (error) {
    next(error);
  }
};
```

you might not belive, however, that's pretty much it, as simple as you see

**that's pretty much it, guys!**

---

**you can reach me here:**

[**Linkedin**](https://linkedin.com/in/faridmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Facebook**](https://facebook.com/fmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Twitter**](https://twitter.com/faridmansimli) &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp; [**Instagram**](https://instagram.com/faridmansimli)

---

**please, buy me a coffe to support this package**.

---

## [![buy me a coffee](https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg)](https://www.buymeacoffee.com/faridmansimli)
