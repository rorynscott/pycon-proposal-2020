| Proposer      | Year | Outcome  | Video   |
| ------------- | ---- | -------- | ------- |
| Rory Scott | 2020 | Accepted | N/A     |

# Proposal

## Title
- Self-Service Infrastructure with Luigi, AIOHTTP, and Jira

## Description

Being a Jira Ticket Monkey is no fun, but being a roadblock to other teams might be even less fun. By leveraging Spotify's Luigi Workflow Engine and SOA/AIOHTTP, we can create a self-service interface through which repetitive tickets are resolved quickly in a standardized way.

Our Platform Team uses Jira Service Desk for customer requests, typically a service request with an approval process (i.e. I need a database, I need a bucket, this IP needs to be whitelisted, etc.). Jira is fine, but how many times have you said to yourself, "It takes me longer to find the ticket I'm looking for, change its status to In Progress, do the work, go back into Jira to find the ticket again, and finally close the ticket?" Our goal was to eliminate many of the manual tasks associated with ticket management, using Python, so that we could focus on improving our platform.

By embracing SOA on our Platform Team and offering infrastructure through our services, we codified the manual steps needed to provision resources using Luigi and directed acyclic graphs, which are triggered by Jira. Compliance is happy because they can approve requests, customers are happy because they aren't slowed down by our team, and our team is happy to focus on more difficult problems than provisioning buckets, databases, and credentials.


## Who and Why (Audience)

- Platform Engineers
- Site Reliability Engineers
- DevOps-minded teams and individuals
- Infrastructure Teams


## Additional Notes

Before joining the platform team at TRHC, I was an engineer automating digital marketing tasks. These problems were solved in similar ways, by providing an API/Service in front of everything we offer, then providing an interface to either the resources directly or a pre-defined workflow.

While not entirely related, I have written about team process and empowerment: https://medium.com/@rorynelsonscott/when-all-you-have-is-one-success-every-problem-looks-like-the-one-before-it-af820554a008

## Personal Notes/Thoughts/Streams
- Platform team is relatively small; 1-4 engineers
- Supports development teams, which has outpaced platform growth due to acquisitions
- Historically, new tasks coming in were handled manually or moderately manually; i.e. terraform modules, bash scripts, cloud formation
- Migrating from AWS to GCP
- Amount of toil is too high, interfering with migration and team development work
- Team is also becoming a bottleneck, preventing teams from moving forward quickly; compliance + manual work + prioritization
- Python, along with SOA and workflow orchestration, to the rescue!
