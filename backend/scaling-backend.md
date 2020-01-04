# How we serve 25M API calls from 10 scalable global endpoints for $150 a month
Source: https://medium.com/free-code-camp/how-we-serve-25m-api-calls-from-10-scalable-global-endpoints-for-150-a-month-911002703280

## Summary
- Initial Tech Stack:
1. Japronto Python Framework
2. Redis
3. AWS EC2 nodes
4. AWS Elastic Loadbalancers
5. Route53 Latency Based Routing
- Chose Japronto over aiohttp and sanic
- 3 EC2 nodes in 3 regions behind ELB loadbalancers with Route53 latency

### Then moved to API Gateway, Lambda, and DynamoDB
- Because of favorable pricing
- Inifinite scale and high throughput
- economically viable to have endpoints in numerous AWS regions
- DynamoDB was cost effective at scale, fast and the firs 200M requests per month were free
- DynamoDB also provided low read latencies
- And this can be sped up with DynamoDB Accelerator (DAX)
