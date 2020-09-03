---
metadata-title: Azure B2C - Samples & Tools for custom policies 
metadata-image: image
metadata-description: Sharing all the samples and tools that can be useful to work on Azure AD B2C.
metadata-createddate: 02/09/2020
metadata-updateddate: 02/09/2020
metadata-tag: B2C
metadata-author: Charles Boudry
---

# Azure B2C - Samples & Tools for custom policies 

## Context

For someone who wants to learn about custom policies in B2C, first step should definitely be to read Microsoft documentation and tutorials.

Microsoft tutorial getting started :
https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-policy-get-started 

Starter pack direct link : 
https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack 

That said, even after that, there is still a bit challenge to master B2C. 

This article intends to help you as best as possible by providing usefull samples and tools.

## Samples

https://github.com/azure-ad-b2c/samples

https://github.com/Azure-Samples/active-directory-b2c-advanced-policies

## Tools

You may find those tools useful to help your B2C pipeline and troubleshooting steps
- To author custom policies, you may use an Azure AD B2C extension for Visual Code :  https://github.com/azure-ad-b2c/vscode-extension 
- To upload policies in Azure wih Custom policy manager :  https://github.com/azure-ad-b2c/custom-policy-manager 
- Collecting Log with Application Insights : https://docs.microsoft.com/en-gb/azure/active-directory-b2c/troubleshoot-with-application-insights 
- To read logs, you may use : 
  - Applications insights log panel : https://docs.microsoft.com/en-us/azure/azure-monitor/platform/data-platform-logs 
  - User Journey Recorder : https://github.com/Azure-Samples/active-directory-b2c-advanced-policies/tree/master/UserJourneyRecorder
  - VS Code extension can be used as well for that
- To decode token : 
  - https://jwt.io/ 
  - https://jwt.ms/
