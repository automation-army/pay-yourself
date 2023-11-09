# pay-yourself
annual salaries indulge poor labor management science and performance

paying people per year instead of per hour eliminates the urgency an individual experiences to *lead themself* by personally figuring out *whats next?*

"job security" then becomes the means to sit back and wait for someone else to tell them what to do

now the budget owner must compensate for this lack of urgency by adding a high-risk, low-output class of worker, the "manager"

the ambiguous charge of managing the performance of others is high-risk because it opens up the possibility to avoid any measurable contribution to production while implicitly accepting credit for other peoples work

in the middleman economy, people always talk about the forest because thats where they like to hide their tree

so finding in this economy middlemanagers who [exploit](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) what shareholders cant measure, i.e. they come up with excuses to schedule and sit in meetings all day, gossip and speculate about the contribution of others, and play nanny among independent adults, is common

#### no ticket, no work, no pay
all production begins with requirements

shareholders are entitled to access a task queue (termed a "backlog" in the software industry) where business requirements are:
1. written by and visible to everyone
1. estimated by potential assignees
1. prioritized by the budget owner

requirement authors add hours worked to tasks they create

and assignees comment task progress daily while adding hours worked to deliver them

if a contributor does not have an assignment, they negotiate the assignment of an available task

if a task is not available, they write the task

no managers

since everyone can subscribe to the progress of a task, excessive middling of this information by middlemanagers gives way to easily-accessible, documented summaries from budget owners

#### wage rate
hourly rates are set in tasks and can be negotiated

contributors publicly negotiate their default hourly rate to minimize the cost of negotiation

a 100/hour contributor can pick up a 50/hour task

a 50/hour contributor may wish to prove their ability to deliver a 100/hour task

#### wage computation
the `pay-yourself` service runs every week, or some other period

tasks worked on by contributors during the period are queried

the per task wage earned by a contributor is computed by multiplying hours worked by the task rate, e.g. 3 hours worked x 50/hour task rate = 150 per task wage

the period wage is computed by adding the wages earned during the period, e.g. 2600

#### wage payment
wages for the period are paid by creating a transaction for each contributor through a transaction service

#### software requirements
1. the `pay-yourslef` service is triggered by cron, and supports being triggered by other events such as "max period wage expense"
1. for each contributor:
    1. [GET issues](https://developer.atlassian.com/cloud/jira/platform/rest/v3/api-group-issue-search/#api-rest-api-3-search-get) where a [worklog entry](https://confluence.atlassian.com/servicemanagementserver/logging-work-on-issues-939937223.html#Loggingworkonissues-Loggingworkonanissue) is added by the contributing user during the period
    1. [GET worklog](https://developer.atlassian.com/cloud/jira/platform/rest/v3/api-group-issue-worklogs/#api-rest-api-3-issue-issueidorkey-worklog-id-get) of issue to parse `timeSpentSeconds` (select "+Show child properties" button under Response section)
    1. compute hourly wage = worklog `timeSpentSeconds` * 60 secs * 60 mins * task rate
    1. add user hourly wages for period
1. [POST payout](https://developer.paypal.com/docs/api/payments.payouts-batch/v1/) to pay for hourly contributions during the period

#### here come the accountants
replacing managers with auditors subjects everyone to serving shareholders and consumers with the same standard of productivity

instead of "reports" accepting a compensated, private, "1-on-1" weekly meeting with their "manager"

everyone, executive included, accepts a compensated, public, weekly task audit with an auditor

"anna, you added 3 hours to this task after writing 2 lines of code. what happened?"

"bob kept status checking me and asking me to join his meeting instead of reading the progress documented in the tasks before submitting his summary to shareholders"

"thank you, anna, shareholders will be grateful for your honesty"

#### summary
useful products and the measurable labor that builds them are important

companies are not

"modern industrial organization and corporate governance" are now just serving as cover for people to acquire budgets, salaries and titles NOT explained by data

manage yourself, pay yourself

#### license

licensed under Apache License, Version 2.0 or MIT license at your option