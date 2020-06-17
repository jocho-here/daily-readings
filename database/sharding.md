# Understanding Database Sharding
Source: https://www.digitalocean.com/community/tutorials/understanding-database-sharding

## Summary
- Sharding is a database architecture pattern related to horizontal partitioning
- Each partition has the same schema and columns, but also entirely different rows
- Vertical partitioning: different columns entirely

### Benefits of Sharding
- Can facilitate horizontal scaling
    - Adding more machines, spreading out the load, allowing more traffic and faster processing
- Vertical scaling has its limit
- Speed up query response times
    - Instead of going through the whole database, it could work over smaller number of rows
- Make an application more reliable by mitigating the impact of outages

### Drawbacks of Sharding
- Complex architecture implementation
    - Much learning curve and could be risky if done incorrectly
- Shards become unbalanced
    - A-M in DB 1, N-Z in DB 2.
    - DB1 becomes the database hotspot
    - System needs to be repaired and resharded
- Very hard to go back to unsharded architecture
- Sharding isn't natively supported by every DB engine

### Implementation
- Key based sharding
    - hash key and distribute based on that
    - Data could be very evenly distributed
- Range based sharding
    - For example, distribute names based on their first character, A-D, E-R, etc.
    - Relatively simple to implement
    - However, this could lead to uneven distribution
- Directory based sharding
    - Maintain a lookup table that uses a shard key to keep track of which shard holds which data
    - The most flexible solution
    - Could make things slow due to the lookup table processing slow
