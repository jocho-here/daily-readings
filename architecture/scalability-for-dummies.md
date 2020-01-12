# Scalability for Dummies
Sources:
- https://www.lecloud.net/post/7295452622/scalability-for-dummies-part-1-clones

## Clones
- Public servers of a scalable web service are hidden behind a load balancer
- First golden rule for scalability: every server contains exactly the same codebase and does not store any user-related data, like sessions or profile pictures, on local disc or memory
- Sessions need to be stored in a centralized data store which is accessible to all your application servers
- Create an image file from one of these servers and super clone that across multiple instances
- Clone: Horizontally scaling

## Database
- If you are using MySQL and if it gets slower and, finally, breaks down, choose NoSQL instead of scaling MySQL further.
- NoSQL DB, like MongoDB, is a better and easier to scale solution.

## Cache
- Cache: a simple in-memory key-value store like Memcached or Redis
- Try to retrieve the data from your cache first and if not present, then try to get it from the main data source.
- Cache is lightning-fast
- Cached Database Queries (Old)
    - Main issue is the expiration
    - Hard to delete acached result when the query is complex
    - When one data is altered, need to delete all those dependent queries
- Cached Objects (New)
    - Let your class assemble a dataset from your database and then store the complete instance of the assembled dataset in the cache
    - Allows you to easily get rid of the object whenever something did change and makes the overall operation of your code faster and more logical
    - Makes asynchronous processing possible
    - The application just consumes the latest cached object and nearly never touches the database anymore
- Objects to cache:
    - user sessions
    - Rendered blog articles (usually cached in client's local memory)
    - activity streams
    - user<->friend relationships

## Asynchronism
- Job queue
- Have a queue of tasks or jobs that a worker can process
- Definitely worth your time to learn about it