## Go Channels and Go Routines

Types of channels:
1. UnBounded
2. Bounded


### UnBounded

Example 1: https://go.dev/play/p/2VrwUi-XDMx

```go
ch := make(chan int)
```

### Bounded

Example 2: https://go.dev/play/p/m4gky1WVmXd

```go
ch := make(chan int, 3)
```


#### Difference b/w bounded and unbounded

In the case of an unbounded channel while signalling the data to channel it is blocked until there is a receiver which makes is `Guaranteed delivery of message`. But in the case of bounded channel receiver need not be present at the time of signalling to the channel. There is no guarantee that message will be delivered

Example 3: https://go.dev/play/p/micO4rsv44p

In the above example, the channel is unbounded and it throws an error at line 10 because there are no receivers at the time of signalling the data to channel, try making it bound like example 2 and run the code