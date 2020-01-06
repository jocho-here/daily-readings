# Service-Oriented Architecture (SOA)
Source: https://medium.com/@SoftwareDevelopmentCommunity/what-is-service-oriented-architecture-fa894d11a7ec
## Summary

### What is SOA?
- SOA is the philosophy of encapsulating application logic in services with a uniformly defined interface and making these publicly available via discovery mechanisms.

### Characteristics of SOA
- Six key characteristics:
1. Business value
2. Strategic goals
3. Intrinsic inter-operability
4. Shared services
5. Flexibility
6. Evolutionary refinement

### SOA patterns
- Three roles in each of the SOA building blocks:
1. Service provider
- Works in conjunction with the service registry
- Debates the whys and hows of the services being offered
- Determines the service category and if there need to be any trading aggrements
2. Service broker, registry, repository
- Makes information regarding the service available to those requesting it
3. Service requester/consumer
- Locates entries in the service registry and then binds them to the service provider
- May or may not be able to access multiple services, depending on the capability of the requester

### Implementing SOA
- SOAP (Simple Object Access Protocol)
- Jini
- COBRA
- REST
- Architectures can "operate independently of specific technologies"

### Why SOA is important
- Creates resuable code
    - Reuse code for different aplications
    - Reduce the development time
- Promotes interaction
    - No longer will communication between platforms be hindered in operation by the languages on which they are built
- Allows for scalability
- Reduced costs

### Microservices vs SOA
- Same concept with different terms