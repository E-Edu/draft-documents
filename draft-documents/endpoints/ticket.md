# Ticket API

**This is not the final document and is subject to change**

### `/ticket`
This endpoint takes the following  `POST` request:
```ts
{
    session: Guid,
    task_id: Guid,
    title: String,
    body: String,
    ticket_type: String
}
```

#### Responses:

```ts
{
    error: String // only present on response codes 40x
}
```

---
### `/ticket/delete`
This endpoint takes the following `DELETE` request

```ts
{
    session: Guid,
    ticket_id: Guid
}
```

#### Responses:

```ts
{
    error: String // only present on response codes 40x
}
```

---
### `/ticket/list`

This endpoint takes the following  `POST` request:

```ts
{
    session: Guid
}
```
#### Responses:

```ts
{
    tickets: [{
        ticket_id: Guid,
        task_id: Guid,
        sender: Guid,
        title: String,
        body: String,
        ticket_type: String

    }],
    error: String // only present on response codes 40x
}
```

---

### `/ticket/edit`

This endpoint takes the following `PUT` request:

```ts
{
    session: Guid,
    ticket_id: Guid,
    comment: String,
    is_troll: Boolean
}
```

#### Responses:

```ts
{
    error: String // only present on response codes 40x
}
```

---

###### [Back](../README.md)