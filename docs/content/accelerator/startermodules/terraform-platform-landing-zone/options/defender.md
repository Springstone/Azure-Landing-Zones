---
title: 13 - Turn off Defender Plans
geekdocCollapseSection: true
weight: 13
---

The Defender Plan policy is enabled by default. If you want to turn off individual Defender plans, you can follow these steps:

1. Update the `management_group_settings.policy_assignments_to_modify` section.
1. Find the `Deploy-MDFC-Config-H224` key and set the enforcement mode of the individual Defender plans to `DoNotEnforce`. See the following example to turn off a subset the Defender plans:

    {{< highlight terraform "linenos=table" >}}
    management_group_settings = {
      ...
      policy_assignments_to_modify = {
        alzroot = {
          policy_assignments = {
            Deploy-MDFC-Config-H224 = {
              parameters = {
                ascExportResourceGroupName                  = "$${asc_export_resource_group_name}"
                ascExportResourceGroupLocation              = "$${starter_location_01}"
                emailSecurityContact                        = "security_contact@replace_me"
                enableAscForServers                         = "DoNotEnforce"
                enableAscForServersVulnerabilityAssessments = "DeployIfNotExists"
                enableAscForSql                             = "DeployIfNotExists"
                enableAscForAppServices                     = "DeployIfNotExists"
                enableAscForStorage                         = "DeployIfNotExists"
                enableAscForContainers                      = "DeployIfNotExists"
                enableAscForKeyVault                        = "DeployIfNotExists"
                enableAscForSqlOnVm                         = "DoNotEnforce"
                enableAscForArm                             = "DeployIfNotExists"
                enableAscForOssDb                           = "DoNotEnforce"
                enableAscForCosmosDbs                       = "DeployIfNotExists"
                enableAscForCspm                            = "DeployIfNotExists"
              }
            }
          }
        }
      }
      ...
    }
    {{< / highlight >}}

{{< hint type=tip >}}
You can find the full list of parameters in the policy assignment [Deploy-MDFC-Config-H224](https://github.com/Azure/Azure-Landing-Zones-Library/blob/main/platform/alz/policy_assignments/Deploy-MDFC-Config-H224.alz_policy_assignment.json) in the library.
{{< /hint >}}