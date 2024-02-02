# Pets App API

## Backend server for the pets app with auth and mongoose relationships

## Entities

```js
User is comprised of the following: 

    email: {
        type: String,
        required: true,
        unique: true,
    },
    hashedPassword: {
        type: String,
        required: true,
    },
    token: String
```

```js
Pet is comprised of the following: 

    name: {
        type: String,
        required: true,
        unique: true,
    },
    type: {
        type: String,
        required: true,
    },
    age: {
        type: Number,
        required: true,
    },
    adoptable: {
        type: Boolean,
        required: true,
        default: false
    },
    toys: [ToySchema],
    owner: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User'
    }

```

```js
Toy is comprised of the following: 

    name: {
        type: String,
        required: true,
        unique: true,
    },
    description: {
        type: String
    },
    isSqueaky: {
        type: Boolean,
        required: true,
        default: false
    },
    condition: {
        type: String,
        enum: ['New', 'Used', 'Disgusting'],
        default: 'New'
    }
```

ERD goes here when ready


## Routes

### Authentication Routes

| Verb   | URI Pattern            | Controller#Action |
|--------|------------------------|-------------------|
| POST   | `/sign-up`             | `users#signup`    |
| POST   | `/sign-in`             | `users#signin`    |
| PATCH  | `/change-password/` | `users#changepw`  |
| DELETE | `/sign-out/`        | `users#signout`   |


### Pet Routes

| Verb   | URI Pattern            | Controller#Action |
|--------|------------------------|-------------------|
| GET   | `/pets`             | `pets#index`    |
| GET   | `/pets/:id`             | `pets#show`    |
| POST   | `/pets`             | `pets#create`    |
| PATCH  | `/pets/:id` | `pets#update`  |
| DELETE | `/pets/:id`        | `pets#delete`   |


### Toy Routes

| Verb   | URI Pattern            | Controller#Action |
|--------|------------------------|-------------------|
| POST   | `/toys/:petId`             | `toys#create`    |
| PATCH  | `/toys/:petId/:toyId`    | `toys#update`  |
| DELETE | `/toys/:petId/:toyId`       | `toys#delete`   |