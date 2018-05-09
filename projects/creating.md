# Creating a Project

We use git for version control in all of our projects, and we use Github to host our repositories.
There are some conventions we use when creating new projects that help keep things organized and easier to maintain.

## Naming

Generally our repos fall into one of three categories: shared code, applications, or service wrappers.

Shared code can be a library intended to be used by one or more other projects, shared configuration, etc.
Whatever it is, generally shared code repos are not intended to be deployed on their own,
rather consumed by other projects that are then deployed, i.e. applications.

Application repos house code that is intended to be deployed as a continually running service.
Some examples are APIs, batch jobs, and workers.

Service wrappers are repos that hold configuration specific to our environments for third party services.
Some examples are MongoDB, RabbitMQ, Micro, Consul, and the ELK stack. These repos are used to deploy these
services into production, configured specifically for our use.

When naming these projects we have a strategy for each:

- For shared code, use a descriptive name for the contents followed by a suffix for the language of the code (`sesac-sdk-ruby`).
- For applications, use a short name that describes the business intent behind the project and can be used for
registering the app as a service, followed by the application type (`mm-models`, `mm-api`, `rd-api`). The name should
not include the language the project is written in.
- For service wrappers, use the lowercase name of the service, followed by `svc` (`mongo-svc`, `elk-svc`).
In some cases, it makes sense to configure more than one third-party service in one repo. When this happens,
choose a name that best describes the primary purpose of the collection of services (`registry-svc`).

Here are some examples:

- `sesac-sdk-ruby` (shared): A software development kit centered around common code for sesac applications.
It is packaged as a ruby gem.
- `mm-api` (application): The API for match-maker, deployed in production to be used by web apps and other applications.
- `mongo-svc` (wrapper): Deployment configuration for MongoDB.
- `registry-svc` (wrapper): Deployment configuration for Micro and Consul. Together they comprise our service registry.

These naming conventions tie the repo to its related components such as its
Jira project/epic, consul service, and even AWS resources. They make it a little easier to, at a glance,
understand what something is and what it relates to.

## Initializing

In addition to code, all repos should have a README.md and CHANGELOG.md. The readme must have a robust description of
the project's purpose as well as any project-specific instructions regarding use, installation, and deployment.
The changelog should, well, track the changes of the project.
We use the changelong conventions [outlined here](https://keepachangelog.com/en/1.0.0/)
