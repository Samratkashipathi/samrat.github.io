## Go Channels and Go Routines

Types of channels:
1. UnBuffered
2. Buffered


### UnBuffered

Example 1: [Go Playground](https://go.dev/play/p/2VrwUi-XDMx)

```go
ch := make(chan int)
```

### Buffered

Example 2: [Go Playground](https://go.dev/play/p/m4gky1WVmXd)

```go
ch := make(chan int, 3)
```


#### Difference b/w Buffered and UnBuffered

In the case of an UnBuffered channel while signalling the data to channel it is blocked until there is a receiver which makes is `Guaranteed delivery of message`. But in the case of Buffered channel receiver need not be present at the time of signalling to the channel. There is no guarantee that message will be delivered

Example 3: https://go.dev/play/p/micO4rsv44p

In the above example, the channel is UnBuffered and it throws an error at line 10 because there are no receivers at the time of signalling the data to channel, try making it Buffered like example 2 and run the code
