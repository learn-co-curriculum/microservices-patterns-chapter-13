## Microservices Patterns Chapter 13 \
 \
Questions:



*   How can we define clear transition periods and avoid the problem of "ongoing transition"?
*   What do we think about separating the presentation tier and the backend? Is that a viable strategy for our team?
*   We appear to be sort of following the Law of Holes in Ironboard for all the legacy JavaScript, and yet it's still there. What...else can we do to kill it?
*   The anti-corruption layer sounds really fascinating. How is that different from an adapter? 

**Migrating away from monolith hell (hereinafter: MH), AKA the art of __Application modernization_! _ AKA the chapter of excessive analogies**

**why migrate away from MH:**

 - "The microservice architecture has, as described in chapter 1, [is dank]."

 - "It has much better maintainability, testability, and deployability, so it accelerates development. The microservice architecture is more scalable and improves fault isolation. It's also much easier to evolve your technology stack."

The years have taught us. Definitely don't:

 - "…do a Big Bang rewrite" (yer boi Martin Fowler has something to say on that: "the only thing a Big Bang rewrite guarantees is a Big Bang!")

**Costs of migrating away from MH:**

 - "[can be oppressive.] As a result, it's likely that the business will only support the adoption of microservices if it solves a significant business problem."

**Justifying moving away from MH:**

_ - "Slow delivery_— [competitors will crush us]"

 - "_Buggy software releases_—[customers think our stuff is crap, and will give us less money]"

 - "_Poor scalability_—[our application is as prepared for the future as a jabroni without a nuclear bunker is for world war III]"

But wait, before you do move away from MH:

_ - "[Don't complicate things and check for easier solutions, dummy."_

**intermission:**


**how to asphyxiate the monolith:**

** - "**Implement new features as services. "

** - "**Separate the presentation tier and backend. "

 - "Break up the monolith by extracting functionality into services. "

to migrate away from MH

 - [be like a parasite. Be like a **strangler application**!] _strangler application(s) _is/are a new application consisting of microservices that you develop by implementing new functionality as services and extracting services from the monolith

 - "Often the tree dies, because either it's killed by the vine or it dies of old age, leaving a tree-shaped vine." - Marty F.

 - [For god's sake, incrementally refactor]

 - Questionable analogy: "[proper MS refactoring is] akin to servicing your car while driving down the highway at 70 mph."

 - "[Make minimal changes to the monolith]"

 - identify what services to split out. Those that:

	- accelerate development

	- solve a performance/scalability/reliability problem

	- enable the extraction of more services

	- sequence services to avoid 'implementing compensating transactions in the monolith'

 - design how services and the monolith will collaborate during this vine stifle. "[Definitely don't not think about the IPC]." Maybe keep a replica of all data events. It is convenient. 

	- ["Consider using an 'anti-corruption' layer, aka an advanced two way serializer on steroids"]

	- Don't forget Sagas - they are ++

**Pitfalls moving away from MH:**



*   _"[Don't be a goof and jump straight for those juicy technical deployment infrastructure refactors]"_
*   "[Extracting services can be tough:]"
    *   splitting the domain model
    *   Refactoring the database

**_Summary _**



*   Before migrating to a microservice architecture, it's important to be sure that your software delivery problems are a result of having outgrown your mono- lithic architecture. You might be able to accelerate delivery by improving your software development process. \

*   It's important to migrate to microservices by incrementally developing a stran- gler application. A strangler application is a new application consisting of microservices that you build around the existing monolithic application. You should demonstrate value early and often in order to ensure that the business supports the migration effort. \

*   A great way to introduce microservices into your architecture is to implement new features as services. Doing so enables you to quickly and easily develop a feature using a modern technology and development process. It's a good way to quickly demonstrate the value of migrating to microservices. \

*   One way to break up the monolith is to separate the presentation tier from the backend, which results in two smaller monoliths. Although it's not a huge improvement, it does mean that you can deploy each monolith independently. This allows, for example, the UI team to iterate more easily on the UI design without impacting the backend. \

*   The main way to break up the monolith is by incrementally migrating function- ality from the monolith into services. It's important to focus on extracting the services that provide the most benefit. For example, you'll accelerate develop- ment if you extract a service that implements functionality that's being actively developed. \

*   Newly developed services almost always have to interact with the monolith. A service often needs to access a monolith's data and invoke its functionality. The monolith sometimes needs to access a service's data and invoke its functionality. To implement this collaboration, develop integration glue, which consists of inbound and outbound adapters in the monolith. \

*   To prevent the monolith's domain model from polluting the service's domain model, the integration glue should use an anti-corruption layer, which is a layer of software that translates between domain models. \

*   One way to minimize the impact on the monolith of extracting a service is to replicate the data that was moved to the service back to the monolith's data- base. Because the monolith's schema is left unchanged, this eliminates the need to make potentially widespread changes to the monolith code base. \


*   Developing a service often requires you to implement sagas that involve the monolith. But it can be challenging to implement a compensatable transaction that requires making widespread changes to the monolith. Consequently, you sometimes need to carefully sequence the extraction of services to avoid imple- menting compensatable transactions in the monolith. \

*   When refactoring to a microservice architecture, you need to simultaneously support the monolithic application's existing security mechanism, which is often based on an in-memory session, and the token-based security mechanism used by the services. Fortunately, a simple solution is to modify the monolith's login handler to generate a cookie containing a security token, which is then for- warded to the services by the API gateway.  \

<p class='util--hide'>View <a href='https://learn.co/lessons/microservices-patterns-chapter-13'>Microservices Patterns Chapter 13</a> on Learn.co and start learning to code for free.</p>
