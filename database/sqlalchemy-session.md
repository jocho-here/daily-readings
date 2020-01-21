# SQLAlchemy Session related knowledge
## When to construct, commit, and clost Session
- tldr
    - Keep the lifecycle of the session separate and external from functions and objects that access and/or manipulate DB data
    - Have a clear notion of where transactions begin and end
    - Keep transactions short, meaning, they end at the series of a sequence of operations, instead of being held open indefinitely
- Session is capable of having a lifespan across many transactions, though only one at a time
    - Transaction scope
    - Session scope
- SQLAlchemy ORM is encouring the developer to establish these two scopes in their application
- A common choice is to tear down the Session at the same time the transaction ends
    - This is a great choice to start out with as it removes the need to consider session scope as separate from transaction scope
- If one is writing a web application, the choice is pretty much established.  A web application is the easiest case because such an application is already constructed around a single, consistent scope - this is the request.
    - Integrating web applications with the Sessions is then the straightforward task of linking the scope of the Session to that of the request
    - The Session can be established as the request begins, or using a lazy initialization pattern which establishes one as soon as it is needed
    - The request then proceeds, with some system in place where application logic can access the current Session in a manner associated with how the actual request object is accessed
    - As the request ends, the Session is torn down as well, usually through the usage of event hooks provided by the web framework
    - The transaction used by the Session may also be committed at this point, or alternatively the application may opt for an explicit commit pattern, only committing for those requests where one is warranted, but still always tearing down the Session unconditionally at the end