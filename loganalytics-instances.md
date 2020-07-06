---
metadata-title: Log Analytics - How many instances
metadata-description: How many instances of Log Analytics you should have is a recurring topic. Here is my synthesis on this question.
metadata-createddate: 24/09/2019
metadata-updateddate: 17/06/2020
metadata-tag: Azure Log Analytics
metadata-author: Charles Boudry
---

# Log Analytics

This articles intends to be a summary of what should be your decision guide for one or multiple log analytics worspaces.

## First rule : fewer is better

Fewer is better:
   - It will be easier to manage
   - You won't have cross queries concern (while they are quite easy to create, imagine the hassle of updating all of them because you are adding yet another workspace)
   - You can leverage Usage Capacity pricing offer if you reach at least 100Go per day

## First mandatory exception : environments

You should at least separate your prod environment workspace from the others env.

Of course you can apply the 1 workspace per environment rule.

## Others acceptable exceptions

   - My ressources span across multiple Azure regions : you may want to consider to put a workspace in the same region to avoid trafic cost.
   - I want to implement segregation of access for multiple teams working on multiple Azure ressources of the same type : Log analytics does not provide row level access so you will need to have multiple workspace to work around that. 
