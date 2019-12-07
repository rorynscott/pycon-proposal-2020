| Proposer      | Year | Outcome  | Video   |
| ------------- | ---- | -------- | ------- |
| Rory Scott | 2020 | TBA | TBA     |

# Proposal

## Title
- Self-Service Infrastructure with Luigi, AIOHTTP, and Jira Service Desk
- Automating Jira Tickets with Luigi and AIOHTTP
- Service Catalog with Luigi and AIOHTTP

## Duration
I prefer a 30 minute slot

## Description

Being a Jira Ticket Monkey is no fun, but being a roadblock to other teams might be even less fun. By leveraging Spotify's Luigi Workflow Engine and SOA/AIOHTTP, we can create a self-service interface through which repetitive tickets are resolved quickly in a standardized way.

Our Platform Team uses Jira Service Desk for customer requests, typically a service request with an approval process (i.e. I need a database, I need a bucket, this IP needs to be whitelisted, etc.). Jira is fine, but how many times have you said to yourself, "It takes me longer to find the ticket I'm looking for, change its status to In Progress, do the work, go back into Jira to find the ticket again, and finally close the ticket?" Our goal was to eliminate many of the manual tasks associated with ticket management, using Python, so that we could focus on improving our platform.


## Who and Why (Audience)

- Platform Engineers
- Site Reliability Engineers
- DevOps-minded teams and individuals
- Infrastructure Teams

## Outline

What is Luigi? Luigi is a workflow engine created by Spotify that addresses "all the plumbing typically associated with long-running batch processes". Its main unit of work is a "Task", which is extremely extensible. Additionally, tasks can have upstream dependencies, meaning they will not be run until the upstream tasks are complete, and tasks can share parameters and output values. Typically, Luigi is used with data pipelines, but the idea of a D.A.G. works really well in our use case too, as we are replacing the steps a human would have to do.

What's a D.A.G.? Directed Acyclic Graph! Define nodes (tasks) and their relationships to other nodes (tasks). For example, if you need to perform a PATCH to a resource and it requires an ID, but you only know the item's name, you can perform a GET first to retrieve the ID, then pipe the ID as an output to the next item in the graph. D.A.G.s also allow for parallelism; if two tasks can be executed at the same time, they simply can be.

Show an example configuration in yaml that Python serializes into a Luigi D.A.G. and how dependencies can be defined along with parameters.

To execute the steps, there are again many tools at our disposal, and we use quite a few different ones depending on the resource. We have been using AIOHTTP for our internal services, primarily as a facade around third-party APIs, which allows us to create an internal contract for a resource, but doesn't tie us to one particular provider depending on the need of our customer. We extended Luigi with an HTTPTask, which takes parameters such as URL, URI, payload, headers, query params, etc., and can make decisions based on a response or status code.

## Additional Notes

## Personal Notes/Thoughts/Streams
- Platform team is relatively small; 1-4 engineers
- Supports development teams, which has outpaced platform growth due to acquisitions
- Historically, new tasks coming in were handled manually or moderately manually; i.e. terraform modules, bash scripts, cloud formation
- Migrating from AWS to GCP
- Amount of toil is too high, interfering with migration and team development work
- Team is also becoming a bottleneck, preventing teams from moving forward quickly; compliance + manual work + prioritization
- Python, along with SOA and workflow orchestration, to the rescue!
