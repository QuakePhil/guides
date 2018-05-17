HOW TO
======

# Start Here
http://trailblazer.to/
> Trailblazer gives you a high-level architecture for web applications. It extends the basic MVC pattern with new
abstractions. Rock-solid conventions that go far beyond database table naming or route paths let you focus on your
application code, minimize bugs and improve the maintainability. The operation abstraction gives us a distinct location
for writing our business logic, while also making that logic more easily testable by providing dependency injection. The
primary components we use are `Operation`, `Representable`, and `Disposable`. To lesser extent, we also use `Cells` and
`Reform`.

https://github.com/ruby-grape/grape
> Our framework for creating REST-like APIs in Ruby. Grape provides a DSL for writing lean, clear endpoints. There is a
lot of functionality in Grape, but we don't use most of it, favoring Trailblazer's functionality for presentation and
response handling.

# SQL
http://sequel.jeremyevans.net/
- Sequel provides thread safety, connection pooling and a concise DSL for constructing SQL queries and table schemas.
- Sequel includes a comprehensive ORM layer for mapping records to Ruby objects and handling associated records.
- Sequel supports advanced database features such as prepared statements, bound variables, stored procedures, savepoints, two-phase commit, transaction isolation, master/slave configurations, and database sharding.
- Sequel currently has adapters for ADO, Amalgalite, IBM_DB, JDBC, MySQL, Mysql2, ODBC, Oracle, PostgreSQL, SQLAnywhere, SQLite3, and TinyTDS.

> Sequel's dataset and API for lower-level database interaction allow us to have more flexibility in our data
interactions. Much of our data does not conform to relational best practices, meaning ActiveRecord is not the best tool
for the job.

# Docker
- https://blog.codeship.com/why-docker/
- https://docs.docker.com/get-started/
- https://blog.codeship.com/using-docker-compose-for-ruby-development/

> All of our production applications run inside docker containers. This provides us the ability to develop in an
environment as close to a production environment as possible. It also means we can maintain and ship
application-specific configuration and dependencies inside our VCS, without having to maintain application-specific
servers.

# Microservices
- https://micro.mu/docs/index.html
- https://github.com/micro/micro/
- https://www.consul.io/

> Instead of maintaining a monolithic API, our API comprises many distinct applications (or modules) running in separate
containers on separate servers. Using namespacing conventions and load balancing, all of these modules are presented as
a single REST-like API from a single URL. However, behind the scenes, each module registers itself as a service with our
service registry (consul), and can use our microservice framework (micro) to contact other services by namespace. This
means no service needs to know the exact address of another, allowing for richer interactions and the ability to compose
new functionality from existing components. This strategy has the added benefit that one module can be stopped, started,
replaced, scaled, etc, without bringing down the entire network.

# Solr
- http://lucene.apache.org/solr/guide/7_2/

> Many of our applications provide the ability to quickly browse and filter data. We implement this by using Solr as our
search index.

# Languages

- [ruby]('./ruby.md')

# Coding Guidelines
- https://robots.thoughtbot.com/sandi-metz-rules-for-developers
