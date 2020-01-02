# Backpressure
Source: https://medium.com/@jayphelps/backpressure-explained-the-flow-of-data-through-software-2350b3e77ce7

## Summary
- Backpressure definition: resistance or force opposing the desired flow of data through software
- Backpressure is when the progress of turning that input to output is resisted in some way, most of the time by the computational speed

### Reading and writing files
- If we give buffer to cover up slow writing speed compared to reading speed, as things to read increase, buffer would increase as well.  It could exceed the amount of available memory.  This is not viable approach.
- Solution: Only read as fast as you can write.  IO libraries do it for you in the concept of "streams" and "pipes"

### Server Communication
- If server A sends more requests (100 rps) than server B could process (75 rps)
- Solution:
1. Buffering 25 rps -> if this persists, server B will run out of memory and fall over
2. Dropping requests -> this is usually not Okay
3. Control the rate in which server A sends requests -> not always viable -> still better to have server A buffer

### Backpressure Strategies
1. Control the producer
- Best option
- Not always possible
2. Buffer
3. Drop
4. Ignore it if it's not a critical issue