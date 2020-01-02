# I'm not feeling the async pressure
- Source: https://lucumr.pocoo.org/2020/1/1/async-pressure/

## Summary
- Async makes it easy to await an operation that can take some time to finish
- But in backpressure management, async makes it worse


### Backpressure
- Backpressure is resistance that opposes the flow of data through a system
- Solutions for backpressure:
1. Buffer
2. Drop
3. Flow control
- Being able to communicate backpressure is crucial

### Bad Defaults
- Imagine an async server that spins up a socket for each connection.
- This could potentially lead to overload

### Waiting vs Waiting to Wait
- Let's say we take set number of concurrent connections.
- We want to let 4 times as many requests be processed as we are expecting that a lot of what the application does is independent of the DB
- One way: make a semaphore with 200 tokens and wait for the semaphore to release a token
- We are back to queueing.
- Some clients would not wait forever
- Instead of waiting blindly, imagine you get a ticket from a machine that tells you when it's your turn
- This way, you can decided to wait or come back later
- So with semaphore, if we could tell how mnay tokens are available, we let the caller know how long to wait for

### Conclusion
- async/await is great but it encourages writing stuff that will behave catastrophically when overloaded
- This async library lets many more developers who previously had little experience with distributed system now have many of the problems of a distributed system even if they only write a single program
- Lack of backpressure is a type of footgun that has a size of a bazooka.
- If you realize too late that you built a monster it will be almost impossible to fix without major changes to the code base because you might have forgotten to make some functions async that should have been
