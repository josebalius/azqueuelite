# azqlite

azqlite is lightweight wrapper around [github.com/Azure/azure-storage-queue-go/azqueue](https://github.com/Azure/azure-storage-queue-go/azqueue) to interact with the Azure Storage Queue service in a simpler and more idiomatic way.

## Install

```
go get github.com/josebalius/azqlite
```

## How to use

### Instantiate a service 
```go
storageService, err := azqlite.NewService(azqlite.Config{
	AccountName: "YOUR_AZURE_STORAGE_ACCOUNT_NAME_HERE",
	AccountKey:  "YOUR_AZURE_STORAGE_ACCOUNT_KEY_HERE",
})
```

### Create a queue
```go
q, err := storageService.CreateQueue(ctx, "test")
```

### Delete a queue
```go
err = s.DeleteQueue(ctx, "test")
```

### Instantiate an existing queue
```go
q := s.NewQueue("test")
```

### Get message count
```go
c, err := q.MessageCount(ctx)
```

### Enqueue a message
```go
m, err := q.Enqueue(ctx, "my message", 1*time.Second, -time.Second)
```

### Dequeue messages
```go
messages, err := q.Dequeue(ctx, 30, 1*time.Second)
```

### Peek messages
```go
messages, err := q.Peek(ctx, 30)
```

### Delete a message
```go
err := q.Delete(ctx, &Message{ID: "1"})
```
