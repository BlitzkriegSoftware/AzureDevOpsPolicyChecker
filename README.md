# AzureDevOpsPolicyChecker

A CI build step to check for compliance to static code rules

## Overview

This is a plug-in that can be added to a Continous-Integration (CI) build to check for conformance to the shop standard

## Configuration File

Notice that RegEx strings may require escaping to make a valid JSON string.
Useful utility: [freeformatter](https://www.freeformatter.com/json-escape.html)

```json
[
    {
        "RuleType": "NuGet",
        "Item": "SecurityCodeScan",
        "Version": "3\\.[0-9]?\\.[0-9]?",
        "StatusCode": "FailBuild"
    },
       {
        "RuleType": "NuGet",
        "Item": "Microsoft.CodeQuality.Analyzers",
        "Version": "[2-9]*\\.[0-9]?\\.[0-9]?",
        "StatusCode": "FailBuild"
    },
       {
        "RuleType": "NuGet",
        "Item": "Swashbuckle.AspNetCore",
        "Version": "[5-9]*\\.[0-9]?\\.[0-9]?",
        "StatusCode": "Ignore"
    },
       {
        "RuleType": "NuGet",
        "Item": "Swashbuckle.AspNetCore.Swagger",
        "Version": "[5-9]?\\.[0-9]?\\.[0-9]?",
        "StatusCode": "Ignore"
    },
       {
        "RuleType": "DotNet",
        "Item": "netcoreapp3.1",
        "Version": "",
        "StatusCode": "Warning"
    },
       {
        "RuleType": "DotNet",
        "Item": "netcoreapp2.1, netcoreapp2.0",
        "Version": "",
        "StatusCode": "FailBuild"
    }
]
```

### Item

The string to match (exact, case sensitive)

### Version

This is a constant or a RegEx, if not applicable can be omitted or set to empty or blank (whitespace)

### Rule Type Codes

|Code|Meaning|
|:--|:--|
|NuGet|Check for presense/absense of a NuGet at a specific version (or higher)|
|DotNet|Check for a specific .NET version(s) (Comma separated)|

### Build Status Codes

|Code|Meaning|
|:--|:--|
|FailBuild|Fail the build if rule fails|
|Warning (default)|Put a warning banner in build output|
|Ignore|Ignore if missing, apply rule if present always a warning|

## Setup in ADO

// TODO

## About ##

* Stuart Williams
* Cloud/DevOps Practice Lead
* Magenic Technologies Inc.
* Office of the CTO
* [stuartw@magenic.com](mailto:stuartw@magenic.com) (e-mail)
* [Blog](http://blitzkriegsoftware.azurewebsites.net/Blog) 
* [LinkedIn](http://lnkd.in/P35kVT) 
* [YouTube](https://www.youtube.com/user/spookdejur1962/videos)
