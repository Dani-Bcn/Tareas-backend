# Project's name REST API
## Description

This is a the backend repository for the React application `HomerWorkforKids`.

---

## Instructions

When cloning the project, change the <code>sample.env</code> file name for <code>.env</code>. The project will run on **PORT 8000**.

Then, run:
```bash
npm install
```
## Scripts

- To start the project run:
```bash
npm run start
```
- To start the project in development mode, run:
```bash
npm run dev
```
- To seed the database, run:
```bash
npm run seed
```
---

## Models

### User

Users in the database have the following properties:

```js
const childSchema = new Schema({

    name:{
        type:String,
        required:true
    },   
    yearOfBirth:{
        type:Number,      
    },
    imageUrl:{
        type:String,      
    },
    tasks: {
        type: [mongoose.Schema.ObjectId],
        ref: 'Task',
      },
    user: {
        type: mongoose.Schema.ObjectId,
        ref: 'User',
      },
    points:{
        type:Number
    },
    pointsCup:{
        type:Number
    },
    cups:{
        type:Number
    },
    goalTasks:{
        type:Number
    },
    taskDone:{
        type:Number
    }
})
module.exports = model("Child", childSchema)
----------------------------
const taskSchema = new Schema({    
    name:{
        type:String,
        required:true
    },
    imageUrl:{
        type:String,
    },
    points:{
        type:Number,
        rquired:true
    }
})

module.exports = model("Task", taskSchema)
--------------------------
const userSchema = new Schema({
  
  email: {
    type: String,
    unique: true,
    required: true
  },
  hashedPassword: {
    type: String,
    required: true
  },
  username: {
    type: String,
    required: true
  },
  role: {
    type: String,
    enum: ['user', 'admin'],
    default: 'user'
  }
},
  {
    timestamps: true
  });

module.exports = model("User", userSchema);
```

---

## API endpoints and usage 

| Action           | Method    | Endpoint             | Req.body                        | Private/Public |
|------------------|-----------|----------------------|---------------------------------|-----------------|
| SIGN UP user     | POST      | /api/v1/auth/signup  | { username, email, password }   |    Public |                 
| LOG IN user      | POST      | /api/v1/auth/login   | { email, password }             |    Public |                  
| GET logged in user   | GET     | /api/v1/auth/me    |   | Private |

---

## Useful links

- [Presentation slides]()
- [Frontend repository]()
- [Frontend deploy]()
- [Deployed REST API]()

