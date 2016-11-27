# Service State

## Stateless



## Stateful

Stateful services genreally display a **lower latency** and **higher throughput**
than the traditional stateless services.
This is due to the fact that stateful services are closer to their data, the hold their data themselves.

For example, consider an online game, if the players and creatures in the game were managed by a stateless service, then whenever somone does anything,
the game would have to load all state from some sort of persistent storage, then act upon that, and save all the state back.

This is ofcourse not a plausible way forward in this scenario as a considerable amount of time would be spent loading and saving state.

Instead, we can build our system as a stateful service.
This means that all or atleast some of the state is already loaded and available to use.

Stateful services can be build using different state strategies.

### Actors


[https://en.wikipedia.org/wiki/Actor_model](https://en.wikipedia.org/wiki/Actor_model)

Implementations:

* Erlang
* Elixir
* Pony
* Akka
* Akka.NET
* Asynkron Go Actor Model

Pros:

* Lightweight, Can be used in the small
* Strong Concurrency Guarantees
* Can be used to model other abstractions

Cons:

* Harder to deal with scale out, more knowledge needed
* Harder to deal with failover, more knowledge needed


### Virtual Actors

The Virtual Actor model differs from the classic actor model in the sense that virtual actors appear to *always exist*.
There is no lifecycle in the same sense as in the classic model.
You simply ask for an actor of a specific type with a specific ID, and the runtime will take care of the rest.

[https://www.microsoft.com/en-us/research/project/orleans-virtual-actors/](https://www.microsoft.com/en-us/research/project/orleans-virtual-actors/)

Implementations:

* Microsoft Orleans
* Microsoft Service Fabric
* Bioware Orbit
* Asynkron Go Actor Model - Cluster

Pros:

* Easy programming model
* Easy to scale out
* Easy to deal with failover

Cons:

* Favors Request Response communication
* Hard to leverage data locality
* No concurrency guarantees, multiple actor/grain activation possible

