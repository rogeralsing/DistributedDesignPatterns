# Consistent Hashing

Consistent Hashing is often used to create a form of affinity between consumers of information and the information itself.
There are many reasons why this is useful, but two common examples are:

## Scalable Clusters

By applying consistent hashing over some form of identifier, you can calculate the target node for a given peice of data.
This is used by databases like Cassandra and Couchbase.
It is also used to enable linear scalability in Microsoft Orleans.

In all of the cases mentioned above, you take an identifier, be it your document Key or the Orleans Grain ID, and then hash it.
Once you have the hash, you can make a lookup over a so called Hash Ring to find out where in your cluster this peice of data belongs.
This way, the system do not need to synchronize or communicate in order to find a given identifier/key.
Some communication is however needed when new nodes **join** or **leave** the cluster.

## Controlling concurrency

Much like in the scalable cluster scenario, you can apply the same technique when there is a need to handle concurrency inside a process.
Instead of distributing load across machines, you can distribute load across workers or threads.
This ensures that only one thread or worker is responsible for writing data given a specific identifier/key.
This prevents race conditions between writes as writes to a specific entity becomes single threaded, while writes to different entities can done in parallel.

The two approaches can be combined in order to scale both up and out.

It is fairly easy to implement this manually, but if possible, use a library or framework or product that does this for you.

Relevant reading:

* https://en.wikipedia.org/wiki/Consistent_hashing
