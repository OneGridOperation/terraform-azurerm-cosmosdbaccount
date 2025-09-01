# [terraform-azurerm-cosmosdbaccount][1]

Manages a CosmosDB (formally DocumentDB) Account.

## Getting Started

- Format and validate Terraform code before commit.

```shell
terraform init -upgrade \
    && terraform init -reconfigure -upgrade \
    && terraform fmt -recursive . \
    && terraform fmt -check \
    && terraform validate .
```

- Always fetch latest changes from upstream and rebase from it. Terraform documentation will always be updated with GitHub Actions. See also [.github/workflows/terraform.yml](.github/workflows/terraform.yml) GitHub Actions workflow.

```shell
git fetch --all --tags --prune --prune-tags \
  && git pull --rebase --all --prune --tags
```

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.8.2 |
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | >= 4.18.0, < 5.0.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | 4.18.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [azurerm_cosmosdb_account.cosmosdb_account](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cosmosdb_account) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_access_key_metadata_writes_enabled"></a> [access\_key\_metadata\_writes\_enabled](#input\_access\_key\_metadata\_writes\_enabled) | (Optional) Is write operations on metadata resources (databases, containers, throughput) via account keys enabled? Defaults to `true`. | `bool` | `true` | no |
| <a name="input_analytical_storage_schema_type"></a> [analytical\_storage\_schema\_type](#input\_analytical\_storage\_schema\_type) | (Optional) The schema type of the Analytical Storage for this Cosmos DB account. Possible values are `FullFidelity` and `WellDefined`. | `string` | `null` | no |
| <a name="input_capabilities_disable_rate_limiting_responses"></a> [capabilities\_disable\_rate\_limiting\_responses](#input\_capabilities\_disable\_rate\_limiting\_responses) | (Optional) Configures the DisableRateLimitingResponses capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_capabilities_enable_mongo"></a> [capabilities\_enable\_mongo](#input\_capabilities\_enable\_mongo) | (Optional) Configures the EnableMongo capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_capabilities_enable_mongo_16mb_document_support"></a> [capabilities\_enable\_mongo\_16mb\_document\_support](#input\_capabilities\_enable\_mongo\_16mb\_document\_support) | (Optional) Configures the EnableMongo16MBDocumentSupport capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_capabilities_enable_mongo_retryable_writes"></a> [capabilities\_enable\_mongo\_retryable\_writes](#input\_capabilities\_enable\_mongo\_retryable\_writes) | (Optional) Configures the EnableMongoRetryableWrites capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_capabilities_enable_serverless"></a> [capabilities\_enable\_serverless](#input\_capabilities\_enable\_serverless) | (Optional) Configures the EnableServerless capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_capabilities_enable_table"></a> [capabilities\_enable\_table](#input\_capabilities\_enable\_table) | (Optional) Configures the EnableTable capability for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_consistency_policy_consistency_level"></a> [consistency\_policy\_consistency\_level](#input\_consistency\_policy\_consistency\_level) | (Required) The Consistency Level to use for this CosmosDB Account. It can be either BoundedStaleness, Eventual, Session, Strong or ConsistentPrefix. | `string` | n/a | yes |
| <a name="input_consistency_policy_max_interval_in_seconds"></a> [consistency\_policy\_max\_interval\_in\_seconds](#input\_consistency\_policy\_max\_interval\_in\_seconds) | (Optional) When used with the Bounded Staleness consistency level, this value represents the time amount of staleness (in seconds) tolerated. Accepted range for this value is `5` - `86400` (1 day). Defaults to `5`. Required when `consistency_level` is set to `BoundedStaleness`. | `number` | `5` | no |
| <a name="input_consistency_policy_max_staleness_prefix"></a> [consistency\_policy\_max\_staleness\_prefix](#input\_consistency\_policy\_max\_staleness\_prefix) | (Optional) When used with the Bounded Staleness consistency level, this value represents the number of stale requests tolerated. Accepted range for this value is `10` – `2147483647`. Defaults to `100`. Required when `consistency_level` is set to `BoundedStaleness`. | `number` | `100` | no |
| <a name="input_enable_automatic_failover"></a> [enable\_automatic\_failover](#input\_enable\_automatic\_failover) | (Optional) Enable automatic fail over for this Cosmos DB account. | `bool` | `false` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | (Optional) Enable the creation of this Cosmos DB account. | `bool` | `true` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | (Required) The name of the environment. | `string` | n/a | yes |
| <a name="input_geo_location_failover_priority"></a> [geo\_location\_failover\_priority](#input\_geo\_location\_failover\_priority) | (Optional) The failover priority of the region. A failover priority of `0` indicates a write region. The maximum value for a failover priority = (total number of regions - 1). Failover priority values must be unique for each of the regions in which the database account exists. Changing this causes the location to be re-provisioned and cannot be changed for the location with failover priority `0`. | `number` | `0` | no |
| <a name="input_geo_location_location"></a> [geo\_location\_location](#input\_geo\_location\_location) | (Optional) The name of the Azure region to host replicated data. | `string` | `""` | no |
| <a name="input_geo_location_zone_redundant"></a> [geo\_location\_zone\_redundant](#input\_geo\_location\_zone\_redundant) | (Optional) Should zone redundancy be enabled for this region? Defaults to `false`. | `bool` | `false` | no |
| <a name="input_key_vault_key_id"></a> [key\_vault\_key\_id](#input\_key\_vault\_key\_id) | (Optional) A versionless Key Vault Key ID for CMK encryption. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_kind"></a> [kind](#input\_kind) | (Optional) Specifies the Kind of CosmosDB to create. Possible values are GlobalDocumentDB and MongoDB. Defaults to GlobalDocumentDB. Changing this forces a new resource to be created. | `string` | `"GlobalDocumentDB"` | no |
| <a name="input_local_authentication_disabled"></a> [local\_authentication\_disabled](#input\_local\_authentication\_disabled) | (Optional) Disable local authentication and ensure only MSI and AAD can be used exclusively for authentication. Defaults to `false`. Can be set only when using the SQL API. | `bool` | `false` | no |
| <a name="input_mongo_server_version"></a> [mongo\_server\_version](#input\_mongo\_server\_version) | (Optional) The Server Version of a MongoDB account. Possible values are `4.2`, `4.0`, `3.6`, and `3.2`. | `string` | `null` | no |
| <a name="input_offer_type"></a> [offer\_type](#input\_offer\_type) | (Optional) Specifies the Offer Type to use for this CosmosDB Account. Currently, this option can only be set to `Standard`. | `string` | `"Standard"` | no |
| <a name="input_override_location"></a> [override\_location](#input\_override\_location) | (Optional) Override the location of the resource. Under normal circumstances, it should not be used. | `string` | `null` | no |
| <a name="input_override_name"></a> [override\_name](#input\_override\_name) | (Optional) Override the name of the resource. Under normal circumstances, it should not be used. | `string` | `null` | no |
| <a name="input_public_network_access_enabled"></a> [public\_network\_access\_enabled](#input\_public\_network\_access\_enabled) | (Optional) Whether or not public network access is allowed for this CosmosDB account. | `bool` | `true` | no |
| <a name="input_resource_group"></a> [resource\_group](#input\_resource\_group) | (Required) The resource group in which to create the resource. | `any` | n/a | yes |
| <a name="input_system_name"></a> [system\_name](#input\_system\_name) | (Required) The systen name which should be used for this resource. Changing this forces a new resource to be created. | `string` | n/a | yes |
| <a name="input_tags"></a> [tags](#input\_tags) | (Optional) A mapping of tags to assign to the resource. | `map(string)` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_azurerm_cosmosdb_account"></a> [azurerm\_cosmosdb\_account](#output\_azurerm\_cosmosdb\_account) | The Azure CosmosDB Account resource. |
<!-- END_TF_DOCS -->

[1]: https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cosmosdb_account
