# Software Engineering

### Explain Agile, Scrum, and Waterfall models.

These are three common software development methodologies.

* **Waterfall Model:**
    * **Principle:** A linear, sequential approach where each phase of development must be completed before the next one can begin.
    * **Phases:** Requirements -> Design -> Implementation -> Verification -> Maintenance.
    * **Characteristics:** Rigid and inflexible. It's often compared to a waterfall, where the process flows in one direction.
    * **Use Cases:** Best for small, well-understood projects with clear, unchanging requirements.
    * **Disadvantages:** Inflexible to change, as new requirements can't be easily incorporated. It's also high-risk, as bugs are only discovered in the late stages of testing.

* **Agile Model:**
    * **Principle:** An iterative and incremental approach that focuses on flexibility, collaboration, and customer feedback.
    * **Characteristics:** Values individuals and interactions over processes and tools, working software over comprehensive documentation, customer collaboration over contract negotiation, and responding to change over following a plan.
    * **Use Cases:** Best for complex projects with evolving requirements.
    * **Disadvantages:** Requires a high degree of collaboration and a cultural shift.

* **Scrum:**
    * **Principle:** A specific, popular framework within the Agile methodology. It's a lightweight, iterative framework for managing complex work.
    * **Characteristics:**
        * **Sprints:** Work is broken into short, fixed-length cycles (typically 1-4 weeks) called sprints.
        * **Roles:** Defines specific roles: Product Owner, Scrum Master, and Development Team.
        * **Artifacts:** Uses artifacts like the product backlog, sprint backlog, and burndown charts.
        * **Meetings:** Has regular meetings: sprint planning, daily stand-ups, sprint review, and sprint retrospective.
    * **Use Cases:** A practical way to implement Agile principles.

---

### What is Version Control? Use of Git?

* **Version Control:**
    * **Definition:** A system that records changes to a file or set of files over time so that you can recall specific versions later.
    * **Function:** It allows multiple people to work on the same project simultaneously without overwriting each other's work. It provides a history of who, what, and when changes were made, making it easy to revert to previous versions if a problem arises.
    * **Types:** Centralized (e.g., SVN) and Distributed (e.g., Git).

* **Git:**
    * **Definition:** A popular **distributed** version control system.
    * **Characteristics:** Every developer has a full copy of the repository on their local machine, including the entire history. This allows them to work offline and makes it very resilient.
    * **Key Features:**
        * **Branching:** Easy to create branches to work on new features or bug fixes in isolation.
        * **Merging:** Simple to merge changes from different branches.
        * **Distributed:** The lack of a single point of failure makes it very robust.
    * **Use:** It is the de-facto standard for version control in software development.

---

### What is CI/CD?

**CI/CD** stands for Continuous Integration and Continuous Deployment/Delivery. It is a set of practices and tools that automate the software development lifecycle to deliver code changes more frequently and reliably.

* **Continuous Integration (CI):**
    * **Principle:** Developers frequently merge their code changes into a central repository (e.g., Git).
    * **Automation:** Automated builds and tests are run on the integrated code to detect and fix integration errors early.
    * **Goal:** To ensure that the codebase is always in a working state.

* **Continuous Delivery (CD):**
    * **Principle:** An extension of CI. After new code is successfully integrated, built, and tested, it is automatically prepared for release to a production-like environment.
    * **Manual Step:** The final deployment to production is a manual, human-initiated step.

* **Continuous Deployment (CD):**
    * **Principle:** A further extension of Continuous Delivery. Every code change that passes all the automated tests is automatically deployed to production without any human intervention.
    * **Goal:** To enable rapid, frequent, and reliable software releases.

---

### Difference between black-box and white-box testing.

These are two fundamental approaches to software testing.

* **Black-Box Testing:**
    * **Principle:** The tester has no knowledge of the internal code, structure, or implementation of the software.
    * **Focus:** The test cases are designed based on the external behavior of the software, its functionality, and the user's perspective. The tester treats the software as a "black box."
    * **Types:** Functional testing, acceptance testing, and performance testing.
    * **Use Cases:** Verifying that the software meets the user's requirements.

* **White-Box Testing:**
    * **Principle:** The tester has full knowledge of the internal code, structure, and implementation of the software.
    * **Focus:** The test cases are designed to test the internal workings, such as code paths, loops, and conditional statements.
    * **Types:** Unit testing, integration testing, and code coverage analysis.
    * **Use Cases:** Finding bugs in the code logic, security vulnerabilities, and ensuring that all parts of the code have been executed.

---

### What is unit testing? Tools?

* **Unit Testing:**
    * **Definition:** A level of software testing where individual units or components of a software application are tested in isolation.
    * **Function:** To verify that each unit of code (e.g., a function, a method, a class) performs as expected.
    * **Process:** Developers write automated tests that call a specific function with a known input and assert that the output is the expected value. These tests are fast, and they are typically run with every code change.
    * **Benefits:** Helps catch bugs early in the development cycle, provides documentation of the code's behavior, and gives developers confidence when refactoring.

* **Tools:**
    * **Java:** JUnit, TestNG.
    * **Python:** unittest, pytest.
    * **JavaScript:** Jest, Mocha, Jasmine.
    * **C#:** NUnit, MSTest.

---

### Explain SOLID principles.

**SOLID** is a set of five design principles that are intended to make software designs more understandable, flexible, and maintainable.

1.  **S - Single-Responsibility Principle (SRP):**
    * **Principle:** A class should have only one reason to change. It should have a single, well-defined responsibility.
    * **Example:** A class that handles both data validation and data storage violates SRP.

2.  **O - Open-Closed Principle (OCP):**
    * **Principle:** A class should be open for extension but closed for modification. You should be able to add new functionality without changing existing code.
    * **Example:** You can add a new type of report without modifying the existing reporting class by using an interface.

3.  **L - Liskov Substitution Principle (LSP):**
    * **Principle:** A subclass should be substitutable for its superclass. If you have a function that takes a base class, it should work correctly with any of its derived classes.
    * **Example:** If you have a `Bird` class, and a `Penguin` subclass, a penguin shouldn't be able to fly. This violates LSP.

4.  **I - Interface Segregation Principle (ISP):**
    * **Principle:** A client should not be forced to depend on interfaces it does not use. Large interfaces should be broken into smaller, more specific ones.
    * **Example:** A single `Worker` interface with methods for `work()`, `eat()`, and `sleep()` could be split into `Workable` and `Eatable` interfaces.

5.  **D - Dependency Inversion Principle (DIP):**
    * **Principle:** High-level modules should not depend on low-level modules. Both should depend on abstractions (interfaces).
    * **Example:** A `BusinessLogic` class should not directly create an object of a `Database` class. Instead, it should depend on a `DatabaseInterface`, and the `Database` class should implement that interface.

---

### What is a design pattern? Examples?

* **Design Pattern:**
    * **Definition:** A general, reusable solution to a commonly occurring problem within a given context in software design. It's a blueprint for solving a problem, not a finished, ready-to-use solution.
    * **Function:** They provide a shared vocabulary among developers, make code more maintainable, and help in creating robust and scalable systems.

* **Examples:**
    * **Creational Patterns:** Focus on object creation mechanisms, increasing flexibility.
        * **Singleton:** Ensures that a class has only one instance and provides a global point of access to it.
        * **Factory Method:** Defines an interface for creating an object, but lets subclasses decide which class to instantiate.
    * **Structural Patterns:** Focus on how classes and objects are composed to form larger structures.
        * **Facade:** Provides a simplified interface to a complex subsystem.
        * **Adapter:** Allows objects with incompatible interfaces to collaborate.
    * **Behavioral Patterns:** Focus on communication and interaction between objects.
        * **Observer:** Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified.
        * **Strategy:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable.

---

### What is REST? Principles of RESTful API?

* **REST (Representational State Transfer):**
    * **Definition:** A software architectural style for building distributed systems, particularly web services. It's not a protocol or a standard; it's a set of guiding principles.
    * **How it works:** REST APIs use standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`, etc.) to interact with resources (e.g., a user, a product) that are identified by a URL (Uniform Resource Locator). The API returns a representation of that resource, typically in JSON or XML format.

* **Principles of a RESTful API:**
    1.  **Statelessness:** The server does not store any client state. Each request from a client to the server must contain all the information needed to understand the request.
    2.  **Client-Server Architecture:** The client and server are separated, allowing them to evolve independently.
    3.  **Uniform Interface:** The system has a consistent and uniform way of interacting with resources, using standard HTTP methods.
    4.  **Cacheability:** Responses from the server should be marked as cacheable or non-cacheable to improve performance.
    5.  **Layered System:** A client can't tell if it's connected directly to the server or to a proxy or load balancer.

---

### Difference between monolith and microservices?

| Feature | Monolith | Microservices |
| :--- | :--- | :--- |
| **Architecture** | A single, large application. All components (UI, business logic, data access) are tightly coupled and run in a single process. | An application is built as a suite of small, independent services. Each service runs in its own process. |
| **Development** | Single codebase, team, and technology stack. | Independent codebases, teams, and technology stacks. |
| **Deployment** | The entire application must be redeployed for any change. | Each service can be deployed independently without affecting others. |
| **Scalability** | Must scale the entire application, even if only one component is a bottleneck. | Can scale individual services that are a bottleneck. |
| **Fault Tolerance**| A failure in one component can bring down the entire application. | A failure in one service does not necessarily affect others. |
| **Complexity** | Simple to start, but becomes complex as the application grows. | Complex to manage, as it involves many services, deployments, and communication protocols. |

---

### What is a load balancer? How is it used?

* **Load Balancer:**
    * **Definition:** A device or software that distributes network traffic and workload across a group of servers (a server farm).
    * **Function:** It acts as a single point of contact for clients and directs incoming requests to one of the backend servers. This prevents any single server from becoming a bottleneck.
    * **How it's used:**
        1.  **Distributes Traffic:** It uses various algorithms (e.g., Round Robin, Least Connections) to decide which server to send a request to.
        2.  **High Availability:** It constantly monitors the health of the backend servers. If a server fails, the load balancer stops sending traffic to it and redirects requests to the remaining healthy servers.
        3.  **Scalability:** Allows a website to handle a large number of requests by adding more servers to the farm without changing the client's connection details.

---

### What is caching? Where would you use it?

* **Caching:**
    * **Definition:** A technique of storing copies of data or files in a temporary location so that they can be accessed more quickly.
    * **Function:** It speeds up data retrieval by reducing the need to fetch data from its original, slower source (e.g., a database or a remote server).
    * **How it works:** The first time a piece of data is requested, it is fetched from the source and stored in a cache. Subsequent requests for the same data are served directly from the cache.

* **Where to use it:**
    * **Web Browsers:** Browsers cache web pages, images, and other assets to speed up subsequent visits to the same website.
    * **Databases:** A database can cache the results of frequently executed queries to improve performance.
    * **CDNs (Content Delivery Networks):** CDNs cache static content (e.g., images, CSS files) on servers located closer to the end-users.
    * **APIs:** An API gateway can cache the results of API calls to reduce the load on the backend services.

---

### Explain horizontal vs. vertical scaling.

These are two different strategies for scaling an application to handle increased load.

* **Vertical Scaling (Scaling Up):**
    * **Principle:** Increasing the resources of a single server.
    * **How it works:** You add more CPU, RAM, or storage to the existing server.
    * **Characteristics:** Simple to implement. Limited by the maximum capacity of a single server. Can be expensive.
    * **Use Cases:** Traditional relational databases often use vertical scaling.

* **Horizontal Scaling (Scaling Out):**
    * **Principle:** Adding more servers to the system.
    * **How it works:** You distribute the workload across multiple servers. This often requires a load balancer.
    * **Characteristics:** More complex to implement. Provides virtually unlimited scalability. Can be more cost-effective.
    * **Use Cases:** Microservices, NoSQL databases, and cloud-native applications are designed for horizontal scaling.

---

### What is eventual consistency?

**Eventual consistency** is a consistency model used in distributed systems (especially NoSQL databases) where, if no new updates are made to a given data item, all reads of that item will eventually return the same value.

* **Characteristics:**
    * **High Availability:** Eventual consistency prioritizes availability over immediate consistency.
    * **Latency:** It has low latency for writes, as a write to one replica doesn't have to wait for all other replicas to be updated.
    * **Inconsistency Window:** There is a period of time, the "inconsistency window," where different replicas of the data may have different values. This window is typically very short.
* **Use Cases:**
    * E-commerce shopping carts: It's acceptable for a user's shopping cart to be slightly out of date for a few seconds.
    * Social media feeds: It's acceptable for a user to not see a friend's new post immediately.

---

### What is a message queue? Why is it used?

* **Message Queue:**
    * **Definition:** A form of asynchronous communication between different software components. It's a buffer that stores messages, allowing a sender to place messages into the queue and a receiver to process them later.
    * **Function:** It decouples the sending and receiving components, meaning the sender doesn't have to wait for the receiver to process the message.

* **Why it's used:**
    1.  **Decoupling:** It separates the components, allowing them to be developed and scaled independently.
    2.  **Asynchronous Processing:** The sender can put a message on the queue and continue its work without waiting for a response. This is useful for long-running tasks like video encoding or sending emails.
    3.  **Load Leveling:** If a service receives a sudden burst of requests, the message queue can absorb the traffic, and the service can process the messages at a steady rate, preventing it from being overwhelmed.
    4.  **Durability:** Messages are stored in the queue, so if a consumer fails, the messages are not lost and can be processed later.

---

### What are API rate limits?

**API rate limits** are a way to control the number of requests a user or an application can make to an API within a specific time period.

* **Function:** They are a crucial part of API design and management.
* **Purpose:**
    * **Protecting the API:** Prevents the API from being overwhelmed by a flood of requests, which could lead to a denial-of-service attack.
    * **Fair Usage:** Ensures that the API is available to all users and that a single user or application doesn't monopolize the resources.
    * **Monetization:** Can be used to enforce a tiered pricing model, where users pay for a higher rate limit.

* **How they work:**
    * The API tracks the number of requests made by a user (identified by their API key or IP address).
    * If the user exceeds the limit (e.g., 100 requests per minute), the API returns an error message (e.g., `HTTP 429 Too Many Requests`).

---

### What is blue-green deployment?

**Blue-green deployment** is a deployment strategy that reduces downtime and risk by running two identical production environments, "Blue" and "Green."

* **How it works:**
    1.  **Blue Environment:** The current production environment that is live and serving traffic.
    2.  **Green Environment:** A new, identical environment where the new version of the application is deployed and tested.
    3.  **Traffic Switch:** Once the new version in the Green environment is verified, the network traffic is switched from the Blue environment to the Green one.
    4.  **Rollback:** If any problems are discovered after the switch, the traffic can be instantly switched back to the old Blue environment, providing a fast and easy rollback.
    5.  **Termination:** The old Blue environment can then be used for the next deployment or terminated.

* **Advantages:** Zero-downtime deployments, fast rollbacks, and a low-risk deployment process.

---

### What is circuit breaker pattern?

The **circuit breaker pattern** is a design pattern used in distributed systems to prevent a failing service from causing cascading failures.

* **Analogy:** It works like a real-life electrical circuit breaker. If a circuit breaker detects a fault, it opens the circuit, stopping the flow of electricity.
* **How it works:**
    1.  **Normal State (Closed):** The system operates normally.
    2.  **Failure Detection:** If a service call fails a certain number of times, the circuit breaker "trips" and moves to the **Open** state.
    3.  **Open State:** While the circuit is open, all calls to the failing service are immediately rejected with an error, without even attempting to connect to the service. This gives the failing service time to recover.
    4.  **Half-Open State:** After a timeout, the circuit moves to a **Half-Open** state. It allows a limited number of test requests to pass through to the service. If these requests succeed, the circuit moves back to the **Closed** state. If they fail, it moves back to the **Open** state.

* **Advantages:** Increases system resilience, prevents cascading failures, and provides a better user experience by failing fast.

---

### What is a reverse proxy?

* **Definition:** A server that sits in front of one or more web servers. It intercepts requests from clients and forwards them to the appropriate backend server.
* **Function:** It acts as a single entry point for all incoming requests.
* **Role:**
    1.  **Load Balancing:** It can distribute requests across multiple backend servers to improve performance and availability.
    2.  **Security:** It hides the identity and IP addresses of the backend servers, protecting them from direct attacks. It can also be used as a firewall.
    3.  **SSL Termination:** It can handle the SSL/TLS encryption and decryption, offloading this computationally intensive task from the backend servers.
    4.  **Caching:** It can cache static content to reduce the load on the backend servers and improve response times.

**Difference from a forward proxy:** A forward proxy acts on behalf of the client to access the internet, while a reverse proxy acts on behalf of the server to handle incoming requests.

### When to use NoSQL over SQL in design?

The decision to use a NoSQL database over a traditional SQL database often comes down to the application's specific requirements for data structure, scalability, and consistency.

**Choose NoSQL when:**

* **You need to scale horizontally:** NoSQL databases are designed to scale out by adding more servers. This is ideal for applications with massive data sets and high traffic volumes that would overwhelm a single SQL server.
* **Your data is unstructured or semi-structured:** NoSQL's flexible schema is perfect for data like user-generated content, IoT sensor data, or social media posts, where the data model is dynamic and can change frequently.
* **You need low latency and high throughput for specific operations:** Key-value stores and document databases are highly optimized for fast reads and writes, making them suitable for caching, real-time analytics, and content delivery.
* **Your application's data model doesn't require complex joins:** NoSQL databases often handle relationships by embedding data or using denormalization. If your queries primarily involve fetching a single document or a small set of related documents, NoSQL is a good fit.
* **Availability is more critical than strong consistency:** Many NoSQL databases offer eventual consistency, which prioritizes keeping the system available and responsive even if some data replicas are temporarily out of sync. This is a good trade-off for applications like e-commerce shopping carts or social media feeds.

**Choose SQL when:**

* **Your data is highly structured and relational:** SQL's rigid schema is perfect for applications where data integrity and well-defined relationships are paramount, like banking systems or inventory management.
* **You need strong transactional consistency (ACID):** SQL databases are built to guarantee that every transaction is atomic, consistent, isolated, and durable.
* **Your application requires complex queries and ad-hoc analysis:** SQL's powerful query language and support for complex joins make it ideal for reporting and business intelligence.

---

### What is schema migration?

**Schema migration** is the process of updating the structure of a database, such as adding or removing a table, changing a column's data type, or adding a new index. It's an essential part of an application's lifecycle, as the data model often evolves with the software.

**Why it's important:**

* **Application evolution:** As a feature is added to an application, the database schema often needs to change to support it.
* **Data integrity:** Schema migrations are used to enforce new data constraints, ensuring that the data remains clean and valid.
* **Version control:** Tools for schema migration (e.g., Flyway, Liquibase) allow developers to version and track database changes, just like they do with application code. This ensures that every developer and every environment (e.g., development, staging, production) has the correct database structure.
* **Automation:** In a CI/CD pipeline, schema migrations are automated to ensure that the database is always in sync with the application code.

In NoSQL databases, schema migration is often simpler or non-existent due to their flexible schema, but it still requires careful planning to ensure the application can handle changes in document structure.

---

### What are common bottlenecks in web apps?

A **bottleneck** is a point of congestion in a system that limits its overall performance. In web applications, bottlenecks are common and can occur at various layers.

* **Database:** The database is a frequent bottleneck.
    * **Poorly optimized queries:** Inefficient SQL queries that perform full table scans can tie up the database server.
    * **Missing indexes:** Without proper indexing, data retrieval can be very slow.
    * **Insufficient connections:** A large number of concurrent requests can overwhelm the database's connection pool.
    * **Locking:** Transactions holding locks for too long can block other requests.
* **Network:**
    * **High latency:** The physical distance between the user and the server can cause delays.
    * **Bandwidth limitations:** The network's capacity might not be enough to handle the volume of traffic.
* **CPU:**
    * **CPU-intensive operations:** Complex calculations, heavy data processing, or poorly written code can consume all the available CPU cycles.
* **Memory:**
    * **Insufficient RAM:** If an application doesn't have enough memory, the system starts swapping to disk, which is significantly slower.
    * **Memory leaks:** A process that continuously consumes more memory without releasing it can eventually crash the system.
* **External APIs:**
    * **Slow third-party services:** A web app waiting for a response from a slow external API can become a bottleneck.
    * **Rate limits:** Hitting the rate limits of an external API can cause requests to fail or be delayed.

---

### Explain CAP theorem in design.

The **CAP theorem** is a fundamental principle in distributed system design. It states that it's impossible for a distributed data store to provide more than two out of three guarantees at the same time:

* **Consistency:** Every read receives the most recent write or an error.
* **Availability:** Every request receives a response, without a guarantee that it contains the most recent version of the data.
* **Partition Tolerance:** The system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes.

In practical distributed systems, network partitions are inevitable. Therefore, you must choose between **Consistency** and **Availability**.

* **Choosing C over A (CP systems):**
    * **Design:** The system will prioritize consistency. If a network partition occurs, the system will become unavailable on the side of the partition that cannot reach the primary data source.
    * **Use cases:** Financial systems, where data accuracy is non-negotiable.

* **Choosing A over C (AP systems):**
    * **Design:** The system will prioritize availability. If a network partition occurs, the system will continue to accept requests on both sides of the partition, but it may return stale data. The data will eventually become consistent once the partition is resolved.
    * **Use cases:** Social media feeds, e-commerce shopping carts, or other systems where a few seconds of inconsistency is acceptable for a better user experience.

The CAP theorem guides the architectural decisions for databases and distributed systems.

---

### What is sharding? When to shard?

**Sharding** is a database scaling technique that involves horizontally partitioning a large database into smaller, independent databases called "shards." Each shard is a complete database that runs on a separate server.

**How it works:**
1.  **Sharding Key:** A column (or a set of columns) is chosen as the sharding key. This key is used to determine which shard a record belongs to.
2.  **Partitioning Scheme:** A function is used to map the sharding key to a specific shard. Common schemes include:
    * **Hash-based:** The sharding key is hashed to determine the shard. This ensures even data distribution.
    * **Range-based:** Data is partitioned based on a range of values (e.g., customers with IDs 1-1000 go to shard 1, 1001-2000 go to shard 2).

**When to shard:**
* **When you've hit the limits of vertical scaling:** You've added as much CPU, RAM, and storage as a single server can handle, and you still have performance problems.
* **When your data set is too large for a single server:** Sharding is a necessity for managing multi-terabyte or petabyte-scale databases.
* **When you need to handle massive traffic:** Sharding distributes the read and write load across multiple servers, preventing a single server from becoming a bottleneck.
* **When you want to reduce latency:** By putting data closer to the users who need it (e.g., sharding by geography), you can reduce network latency.

Sharding adds complexity to the system, so it should be considered a last resort after other optimizations like indexing and caching.

---

### How does distributed logging work?

In a monolithic application, all logs are written to a single file, which is easy to manage. However, in a distributed system (like a microservices architecture), logs are generated by many different services, each running on a separate server. **Distributed logging** is the process of collecting, centralizing, and analyzing logs from all these services.

**How it works:**
1.  **Log Generation:** Each service generates logs in a structured format (e.g., JSON). The logs contain important information like timestamps, service name, log level, and the message itself.
2.  **Log Collection:** A lightweight agent (e.g., Fluentd, Logstash) runs on each server and collects the logs.
3.  **Centralization:** The collected logs are streamed to a centralized logging system. This system acts as a single point of storage and analysis.
4.  **Storage and Indexing:** The centralized system stores the logs and indexes them to enable fast searching.
5.  **Analysis and Visualization:** Developers and operators can use a dashboard (e.g., Kibana, Grafana) to search, filter, and visualize the logs from all services in one place.

**Benefits:**
* **Troubleshooting:** It makes it much easier to debug a problem that spans multiple services.
* **Monitoring:** It provides a holistic view of the system's health and performance.
* **Auditing:** It provides a record of all events that happened in the system.

---

### How do you debug a system in production?

Debugging a system in production is a critical skill, as problems often appear in the real world that are difficult to reproduce in a development environment.

1.  **Centralized Logging and Monitoring:**
    * **Start with the logs:** The first step is to check the centralized logging system. Look for error messages, stack traces, and unusual events. A good logging system will allow you to trace a single request across multiple services.
    * **Check the dashboards:** Use a monitoring system (e.g., Prometheus, Datadog) to check for a sudden spike in CPU usage, memory consumption, or error rates. This can help you pinpoint the problematic service.

2.  **Health Checks and Probes:**
    * Use health checks to see if a service is up and running. A failure in a health check can indicate a problem.

3.  **Reproduce the Issue (Safely):**
    * If possible, try to reproduce the issue in a staging or testing environment. If you can't, use a copy of the production data to simulate the problem.

4.  **Debugging Tools:**
    * **Profiling:** Use a profiler to find performance bottlenecks, such as a function that is taking too long to execute.
    * **Tracing:** Use a distributed tracing tool (e.g., Jaeger, Zipkin) to visualize the flow of a single request across all services. This is invaluable for debugging microservices.

5.  **Re-deploy and Rollback:**
    * If the issue is caused by a recent deployment, a quick rollback to the previous version is often the fastest way to restore service.

6.  **Avoid live debugging:** Avoid making changes directly in the production environment. Instead, use the logs, metrics, and tools to diagnose the problem, fix it in a development environment, and then deploy the fix.

---

### Explain service discovery.

In a microservices architecture, services are often ephemeral and change their IP addresses frequently. **Service discovery** is the process of automatically finding the network location (IP address and port) of a service.

**Why it's needed:**
* **Dynamic environment:** Services can be created, destroyed, and scaled up or down at any time. A service needs to know where its dependencies are.
* **Decoupling:** It decouples services from their physical locations, making the system more flexible and resilient.

**How it works:**
1.  **Service Registry:** A central database (the service registry) stores the location of all available services.
2.  **Service Registration:** When a new service instance starts, it registers itself with the service registry, providing its name, IP address, and port number. It also periodically sends a "heartbeat" to let the registry know that it's still alive.
3.  **Service Discovery:** When a client service needs to call another service, it queries the service registry to get the network location of the dependency.
4.  **Deregerstration:** If a service instance becomes unhealthy or is shut down, it is removed from the registry.

**Methods of Service Discovery:**
* **Client-Side:** The client queries the service registry directly.
* **Server-Side:** A load balancer or a router queries the service registry and forwards the request to the correct service instance.

---

### How do CDN and edge computing help?

* **CDN (Content Delivery Network):**
    * **Definition:** A geographically distributed network of proxy servers and data centers.
    * **How it helps:** CDNs cache static content (e.g., images, CSS files, videos) on servers located closer to the end-users. When a user requests this content, it's served from the nearest CDN server instead of the origin server.
    * **Benefits:**
        * **Reduced latency:** Content is delivered faster to users.
        * **Reduced load on the origin server:** The origin server only has to serve dynamic content.
        * **Improved fault tolerance:** If the origin server goes down, the CDN can still serve the cached content.

* **Edge Computing:**
    * **Definition:** A distributed computing paradigm that brings computation and data storage closer to the source of the data (the "edge" of the network), instead of relying on a centralized cloud.
    * **How it helps:** It allows applications to run at the network edge.
    * **Benefits:**
        * **Real-time processing:** It's ideal for applications that require very low latency, such as autonomous vehicles or industrial IoT.
        * **Reduced bandwidth:** It reduces the amount of data that needs to be sent to a centralized cloud.
        * **Increased privacy:** Data can be processed and filtered at the edge, reducing the need to send sensitive information to the cloud.

---

### What is rate limiting and throttling?

**Rate limiting** and **throttling** are techniques used to control the rate of requests to an API or a service. They are often used interchangeably, but there's a subtle difference.

* **Rate Limiting:**
    * **Definition:** A hard limit on the number of requests a user can make within a specific time window.
    * **Function:** It is a security and availability mechanism. Once a user hits the rate limit, the service will reject all subsequent requests from that user until the time window expires.
    * **Example:** "You can make 100 requests per minute." If you make 101 requests in that minute, the 101st request will be rejected.

* **Throttling:**
    * **Definition:** A softer limit that slows down the user's request rate, rather than rejecting it outright.
    * **Function:** It is a performance and fair usage mechanism. The service will queue the user's requests and process them at a fixed rate, ensuring that no single user can monopolize the service.
    * **Example:** "We will process your requests at a rate of 10 per second. If you send 20 requests in a second, the last 10 will be queued and processed in the next second."

Both techniques are crucial for building robust and fair APIs.

---

### What is observability in systems?

**Observability** is a concept in software engineering that describes how well a system's internal state can be inferred from its external outputs. A system is considered "observable" if you can understand what's happening inside it without needing to deploy new code or custom debugging tools.

**The three pillars of observability:**
1.  **Logs:** A time-stamped record of events that happened in the system. Logs are useful for understanding what happened and why.
2.  **Metrics:** A numerical representation of data measured over time. Metrics are useful for understanding the system's performance and health (e.g., CPU usage, error rates).
3.  **Traces:** A record of the full path of a single request as it flows through a distributed system. Traces are invaluable for debugging microservices and finding performance bottlenecks.

**Why it's important:**
* **Debugging:** Observability makes it easier to diagnose and fix problems in complex systems.
* **Monitoring:** It provides a deep understanding of the system's behavior and performance.
* **Proactive maintenance:** By analyzing trends in metrics, you can identify potential problems before they become critical.

---

### How does authentication/authorization work in design?

**Authentication** and **Authorization** are two distinct but related security concepts.

1.  **Authentication (Who you are?):**
    * **Definition:** The process of verifying the identity of a user or a service.
    * **How it works:** A user provides a credential (e.g., a username and password, an API key, a token). The system verifies that the credential is valid.
    * **Mechanisms:**
        * **Sessions and Cookies:** A user logs in, and the server creates a session and a session ID stored in a cookie.
        * **Tokens (e.g., JWT):** A user logs in, and the server issues a signed token (JWT). The client includes this token with every subsequent request. The server can verify the token without a database lookup.

2.  **Authorization (What you can do?):**
    * **Definition:** The process of determining what an authenticated user is permitted to do.
    * **How it works:** Once a user's identity is confirmed, the system checks their permissions to determine if they can perform a specific action (e.g., read a file, delete a record).
    * **Mechanisms:**
        * **Role-Based Access Control (RBAC):** Users are assigned roles (e.g., "admin," "editor," "viewer"), and each role has a set of permissions.
        * **Attribute-Based Access Control (ABAC):** Permissions are granted based on a user's attributes (e.g., department, location) and the resource's attributes (e.g., type of document, confidentiality level).

In a microservices design, a gateway service often handles authentication and passes the user's identity and roles to the downstream services, which then handle the authorization checks.
