# Task API

**This is not the final document and is subject to change**

### `/task`
This endpoint takes the following `POST` body:
```ts
{
    session: Guid,
    task: String,
    taskType: String,
    necessaryPoints: Number,
    subject: String,
    module: String,
    lecture: String,
    difficulty: String,
    solutions: Array<String>,
    fake_solutions: Array<String>
}
```

#### Responses:
```ts
{
    error: String // only present on response codes 40x
}
```

---

### `/task/search`
This endpoint takes the following `POST` body:
```ts
{
    session: Guid,
    subject: String,
    module: String,
    lecture: String,
}
```

#### Responses: 

```ts
{
    tasks: [{
        task_id: Number,
        task: String,
        taskType: String,
        necessaryPoints: Number,
        subject: String,
        module: String,
        lecture: String,
        difficulty: String,
        author: Guid
    }],
    error: String // only present on response codes 40x
}
```

The response will return a list of tasks in case the search was successful and a error `String` in case a [Error](errors.md) ocurred.

---

### `/task/check`

This endpoint takes the following `POST` body:
```ts
{
    session: Guid,
    user_solution: Array<String>
}
```

#### Responses: 

```ts
{
    right: Boolean, // only present on response codes 20x
    error: String // only present on response codes 40x
}
```


---

### `/task/getNext`

This endpoint is used to get the next task, that is based on the last task, to continue with more tasks in that context. Eventually this will return a final task. 

This endpoint takes the following `GET` body:

```ts
{
    session: Guid,
    last_task_id: Number
}
```

#### Responses: 

```ts
{
    new_task:
    {
        task_id: Number,
        task: String,
        taskType: String,
        necessaryPoints: Number,
        subject: String,
        module: String,
        lecture: String,
        difficulty: String,
        author: Guid
    }
    error: String // only present on response codes 40x
}
```

---

### `/task/verify`
This endpoint takes the following `POST` body:
```ts
{
    session: Guid,
    taskId: Number
}
```

#### Responses: 

```ts
{
    error: String // only present on response codes 40x
}
```

---

### `/task/getPendingTasks`
This endpoint takes the following `GET` body:
```ts
{
    session: Guid
}
```

#### Responses: 

```ts
{
    error: String // only present on response codes 40x
}
```

---

### `/task`
This endpoint takes the following `GET` body:
```ts
{
    session: Guid
}
```
This will return the list of tasks a user created.

#### Responses:

```ts
{
    tasks: Array<{
        task_id: Number,
        rating: Number,
        task: String,
        taskType: String,
        necessaryPoints: Number,
        subject: String,
        module: String,
        lecture: String,
        difficulty: String,
    }>
    error: String // only present on response codes 40x
}
```

---

###### [Back](../README.md)
