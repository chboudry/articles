---
title: Azure Disk - Benchmark
image: automation
description: Describes the different methods for starting a runbook in Azure Automation from another runbook and sharing information between them.
createddate: 01/17/2019
updateddate: 01/17/2019
tag: Azure
author: Charles Boudry
---

# Azure Disk - Benchmark

It is a recommended practice in Azure Automation to write reusable, modular runbooks with a discrete function that is by other runbooks. A parent runbook often calls one or more child runbooks to perform required functionality. There are two ways to call a child runbook, and each has distinct differences that you 
