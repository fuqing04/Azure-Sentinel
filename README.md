
# Microsoft Sentinel and Microsoft 365 Defender

Welcome to the unified Microsoft Sentinel and Microsoft 365 Defender repository! This repository contains out-of-the-box detections, exploration queries, hunting queries, workbooks, playbooks, and much more to help you get started with Microsoft Sentinel and secure your environment. The hunting queries also include Microsoft 365 Defender queries for advanced hunting scenarios across both products.

- 📋 [Submit an issue](https://github.com/Azure/Azure-Sentinel/issues) to request new samples or resources
- 📖 Visit the repository [wiki](https://aka.ms/threathunters) to learn how to contribute
- 📧 Contact us at [AzureSentinel@microsoft.com](mailto:AzureSentinel@microsoft.com) with questions or feedback

## Table of Contents

- [Repository Contents](#repository-contents)
- [Resources](#resources)
- [Feedback and Support](#feedback-and-support)
- [Contribution Guidelines](#contribution-guidelines)
  - [Getting Started](#getting-started)
  - [General Steps](#general-steps)
  - [Pull Request Process](#pull-request-process)
  - [PR Validation Checks](#pr-validation-checks)
  - [Running Validations Locally](#running-validations-locally)
- [Code of Conduct](#code-of-conduct)

## Repository Contents

| Folder | Description |
|--------|-------------|
| [Detections](Detections/) | Out-of-the-box analytic rule templates for Microsoft Sentinel |
| [Hunting Queries](Hunting%20Queries/) | Hunting queries for proactive threat hunting in Microsoft Sentinel and Microsoft 365 Defender |
| [Playbooks](Playbooks/) | SOAR automation playbooks built on Azure Logic Apps |
| [Workbooks](Workbooks/) | Interactive dashboards for visualizing security data |
| [Parsers](Parsers/) | KQL functions for normalizing data from various sources |
| [DataConnectors](DataConnectors/) | Data connector definitions for ingesting data into Microsoft Sentinel |
| [Solutions](Solutions/) | Packaged security content by product or domain |
| [Notebooks](Notebooks/) | Jupyter notebooks for advanced investigation and hunting |
| [Sample Data](Sample%20Data/) | Sample datasets for testing queries and detections |
| [Tools](Tools/) | Utilities to assist with content development and analysis |
| [ASIM](ASIM/) | Advanced Security Information Model (ASIM) parsers and content |

## Resources

- [Microsoft Sentinel documentation](https://go.microsoft.com/fwlink/?linkid=2073774&clcid=0x409)
- [Microsoft 365 Defender documentation](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-365-defender?view=o365-worldwide)
- [Security Community Webinars](https://aka.ms/securitywebinars)
- [Getting started with GitHub](https://help.github.com/en#dotcom)

## Feedback and Support

We value your feedback. Here are the channels available to you:

| Channel | Purpose |
|---------|---------|
| [Microsoft Sentinel Tech Community](https://techcommunity.microsoft.com/t5/microsoft-sentinel/bd-p/MicrosoftSentinel) | General Q&A for SIEM and SOAR |
| [Microsoft 365 Defender Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection) | General Q&A for XDR |
| [Microsoft Sentinel feedback forums](https://feedback.azure.com/d365community/forum/37638d17-0625-ec11-b6e6-000d3a4f07b8) | Product feature requests |
| [Bug report](https://github.com/Azure/Azure-Sentinel/issues/new?assignees=&labels=&template=bug_report.md&title=) | Report product or contribution bugs |
| [Feature request](https://github.com/Azure/Azure-Sentinel/issues/new?assignees=&labels=&template=feature_request.md&title=) | General feedback on community and contribution process |

## Contribution Guidelines

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit [https://cla.microsoft.com](https://cla.microsoft.com).

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

For full contribution details, refer to the ["Get Started"](https://github.com/Azure/Azure-Sentinel/wiki#get-started) section of the project [wiki](https://aka.ms/threathunters).

### Getting Started

> **First-time contributors:** Follow the [general GitHub fork guidance](https://docs.github.com/github/getting-started-with-github/fork-a-repo) or the [Sentinel-specific getting started guide](GettingStarted.md) before cloning the repository.

### General Steps

You can contribute via several methods:

**Option 1 — GitHub web interface:**
1. Browse to the folder you want to upload your file to
2. Choose **Upload Files** and select your file
3. Create your own branch and submit a Pull Request for review

**Option 2 — Local development tools** ([GitHub Desktop](https://docs.github.com/en/desktop/overview/getting-started-with-github-desktop), [Visual Studio](https://visualstudio.microsoft.com/vs/), or [VS Code](https://code.visualstudio.com/?wt.mc_id=DX_841432)):
1. [Fork the repo](https://docs.github.com/github/getting-started-with-github/fork-a-repo)
2. [Clone the repo](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)
3. [Create your own branch](https://help.github.com/en/desktop/contributing-to-projects/creating-a-branch-for-your-work)
4. Make your additions or updates
5. Merge the master branch back into your branch before pushing
6. [Push your changes to GitHub](https://help.github.com/en/github/using-git/pushing-commits-to-a-remote-repository)

### Pull Request Process

1. [Submit a Pull Request (PR)](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) after pushing your changes
2. Provide a clear description of the proposed changes so reviewers can understand the purpose and scope
3. Monitor the [Pull Requests](https://github.com/Azure/Azure-Sentinel/pulls) page for reviewer comments
4. Address any review comments by updating your branch, or explain why no change is needed, then resolve the comment

### PR Validation Checks

All pull requests trigger automated validation checks. The sections below describe each check and how to interpret failures.

#### Detection Template Structure Validation

A structure validation runs to confirm all required parts of the YAML schema are present. See the [contribution guidelines](https://github.com/Azure/Azure-Sentinel/wiki/Contribute-to-Sentinel-GitHub-Community-of-Queries#now-onto-the-how) for the required schema.

Example failure (missing `entityMappings` section):

```
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.95]     Kqlvalidations.Tests.DetectionTemplateStructureValidationTests.Validate_DetectionTemplates_HaveValidTemplateStructure(detectionsYamlFileName: "ExcessiveBlockedTrafficGeneratedbyUser.yaml") [FAIL]
  X Kqlvalidations.Tests.DetectionTemplateStructureValidationTests.Validate_DetectionTemplates_HaveValidTemplateStructure(detectionsYamlFileName: "ExcessiveBlockedTrafficGeneratedbyUser.yaml") [104ms]
  Error Message:
   Expected object to be <null>, but found System.ComponentModel.DataAnnotations.ValidationException with message "An old mapping for entity 'AccountCustomEntity' does not have a matching new mapping entry."
```

#### KQL Syntax Validation

A KQL syntax validation runs against all queries in each template. If this check fails, open the Azure Pipeline link from the **Checks** tab of your PR to see which test failed and why.

![Azure Pipeline link](.github/Media/Azurepipeline.png)

![Pipeline Tests Tab](.github/Media/PipelineTestsTab.png)

Example failure:

```
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:01.81]     Kqlvalidations.Tests.KqlValidationTests.Validate_DetectionQueries_HaveValidKql(detectionsYamlFileName: "ExcessiveBlockedTrafficGeneratedbyUser.yaml") [FAIL]
  X Kqlvalidations.Tests.KqlValidationTests.Validate_DetectionQueries_HaveValidKql(detectionsYamlFileName: "ExcessiveBlockedTrafficGeneratedbyUser.yaml") [21ms]
  Error Message:
   Template Id:fa0ab69c-7124-4f62-acdd-61017cf6ce89 is not valid Errors:The name 'SymantecEndpointProtection' does not refer to any known table, tabular variable or function., Code: 'KS204', Severity: 'Error', Location: '67..93',The name 'SymantecEndpointProtection' does not refer to any known table, tabular variable or function., Code: 'KS204', Severity: 'Error', Location: '289..315'
```

If you are using a custom log table (not defined in all workspaces by default), verify your table schema is defined as a JSON file in `.script/tests/KqlvalidationsTests/CustomTables/`.

**Example `tablexyz.json`:**
```json
{
  "Name": "tablexyz",
  "Properties": [
    {
      "Name": "SomeDateTimeColumn",
      "Type": "DateTime"
    },
    {
      "Name": "SomeStringColumn",
      "Type": "String"
    },
    {
      "Name": "SomeDynamicColumn",
      "Type": "Dynamic"
    }
  ]
}
```

#### Detection Schema Validation

The schema validation checks the detection's frequency and period, trigger type and threshold, and validity of connector IDs (see the [valid connector IDs list](https://github.com/Azure/Azure-Sentinel/blob/master/.script/tests/detectionTemplateSchemaValidation/ValidConnectorIds.json)). An incorrect format or missing attribute will produce an informative failure message. Refer to existing approved detections as a formatting reference.

### Running Validations Locally

Run validations before submitting a PR to catch issues early. You need the [.NET SDK](https://dotnet.microsoft.com/download) installed (supports all platforms).

**KQL Validation:**
```shell
cd Azure-Sentinel/.script/tests/KqlvalidationsTests/
dotnet test
```

**Detection Schema Validation:**
```shell
cd Azure-Sentinel/.script/tests/DetectionTemplateSchemaValidation/
dotnet test
```

A successful KQL validation run looks like this:

```
Test Run Successful.
Total tests: 171
     Passed: 171
 Total time: 25.7973 Seconds
```

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
