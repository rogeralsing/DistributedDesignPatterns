# Orchestrating Services

## Domain Events

One of the dominant approaches for this is to use domain events.
Each service publish events regarding what have happened and other services can subscribe to those events. 
This goes hand in hand with the concept of smart endpoints, dumb pipes that is described by Martin Fowler here: http://martinfowler.com/articles/microservices.html#SmartEndpointsAndDumbPipes

![domainevents.png](domainevents.png)

## Proxy

Another ´common apporach is to wrap the business flow in its own service. 
The proxy orchestrates the interaction between the microservices like shown in the below picture:

![proxy.png](proxy.png)
