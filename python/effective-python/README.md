# Effective Python
Notes from reading Effective Python, written by Brett Slatkin

## Notes

### Chapter 1
#### Prefer Multiple Assignment Unpacking Over Indexing
- Use unpacking in swapping
    - ```
      a = [1,2,3,4]
      a[1], a[2] = a[2], a[1]
      ```
- Prefer `enumerate` over range
   - `enumerate` even allow us to start at the index 1
  - ```python
    snacks = [('bacon', 350), ('donut', 240), ('muffin', 190)]
    for rank, (name, calories) in enumerate(snaks, 1):
        print(f'#{rank}: {name} has {calories} calories')
    ```