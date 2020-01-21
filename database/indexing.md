# Indexing in Database
Source: https://www.geeksforgeeks.org/indexing-in-databases-set-1/

## Summary
- Indexing is a way to optimize the performance of a DB by minimizing the number of disk accesses required when a query is processed
- Indexes are created using a few database columns
    - The first column is the Search key (copy of the primary key or condidate key) of the table.  These values are stored in sorted order so that the corresponding data can be accessed quickly
    - The second column is the Data Reference or Pointer that holds the address of the disk block for that particular key value
- The indexing has various attributes
    - Access Types
        - type of access such as value based search, range access, etc
    - Access Time
        - time needed to find particular data element or set of elements
    - Insertion Time
        - time taken to find the appropriate space and insert a new data
    - Deletion Time
        - time taken to find an item and delete it as well as updated the index structure
    - Space Overhead
        - Additional space required by the index