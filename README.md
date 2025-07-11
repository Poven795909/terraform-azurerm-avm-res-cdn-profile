<!-- BEGIN_TF_DOCS -->
# terraform-azurerm-avm-res-cdn-profile

Module for Azure CDN Profile (Azure Front Door and CDN)

> [!IMPORTANT]
> As the overall AVM framework is not GA (generally available) yet - the CI framework and test automation is not fully functional and implemented across all supported languages yet - breaking changes are expected, and additional customer feedback is yet to be gathered and incorporated. Hence, modules **MUST NOT** be published at version `1.0.0` or higher at this time.
>
> All module **MUST** be published as a pre-release version (e.g., `0.1.0`, `0.1.1`, `0.2.0`, etc.) until the AVM framework becomes GA.
>
> However, it is important to note that this **DOES NOT** mean that the modules cannot be consumed and utilized. They **CAN** be leveraged in all types of environments (dev, test, prod etc.). Consumers can treat them just like any other IaC module and raise issues or feature requests against them as they learn from the usage of the module. Consumers should also read the release notes for each version, if considering updating to a more recent version of a module to see if there are any considerations or breaking changes etc.

<!-- markdownlint-disable MD033 -->
## Requirements

The following requirements are needed by this module:

- <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) (>= 1.9, < 2.0)

- <a name="requirement_azapi"></a> [azapi](#requirement\_azapi) (>= 1.13, < 3)

- <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) (~> 4.0)

- <a name="requirement_modtm"></a> [modtm](#requirement\_modtm) (~> 0.3)

- <a name="requirement_random"></a> [random](#requirement\_random) (>= 3.5.0)

## Resources

The following resources are used by this module:

- [azapi_resource.front_door_profile](https://registry.terraform.io/providers/Azure/azapi/latest/docs/resources/resource) (resource)
- [azurerm_cdn_endpoint.endpoints](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_endpoint) (resource)
- [azurerm_cdn_endpoint_custom_domain.cds](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_endpoint_custom_domain) (resource)
- [azurerm_cdn_frontdoor_custom_domain.cds](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_custom_domain) (resource)
- [azurerm_cdn_frontdoor_custom_domain_association.association](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_custom_domain_association) (resource)
- [azurerm_cdn_frontdoor_endpoint.endpoints](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_endpoint) (resource)
- [azurerm_cdn_frontdoor_firewall_policy.wafs](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_firewall_policy) (resource)
- [azurerm_cdn_frontdoor_origin.origins](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_origin) (resource)
- [azurerm_cdn_frontdoor_origin_group.origin_groups](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_origin_group) (resource)
- [azurerm_cdn_frontdoor_route.routes](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_route) (resource)
- [azurerm_cdn_frontdoor_rule.rules](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_rule) (resource)
- [azurerm_cdn_frontdoor_rule_set.rule_set](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_rule_set) (resource)
- [azurerm_cdn_frontdoor_secret.frontdoorsecret](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_secret) (resource)
- [azurerm_cdn_frontdoor_security_policy.security_policies](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/cdn_frontdoor_security_policy) (resource)
- [azurerm_dns_cname_record.cdn](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/dns_cname_record) (resource)
- [azurerm_management_lock.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/management_lock) (resource)
- [azurerm_monitor_diagnostic_setting.cdn_endpoint_diag](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/monitor_diagnostic_setting) (resource)
- [azurerm_monitor_diagnostic_setting.front_door_diag](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/monitor_diagnostic_setting) (resource)
- [azurerm_monitor_metric_alert.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/monitor_metric_alert) (resource)
- [azurerm_role_assignment.this](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/role_assignment) (resource)
- [modtm_telemetry.telemetry](https://registry.terraform.io/providers/azure/modtm/latest/docs/resources/telemetry) (resource)
- [random_uuid.telemetry](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/uuid) (resource)
- [azapi_client_config.current](https://registry.terraform.io/providers/Azure/azapi/latest/docs/data-sources/client_config) (data source)
- [azurerm_client_config.telemetry](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/client_config) (data source)
- [modtm_module_source.telemetry](https://registry.terraform.io/providers/azure/modtm/latest/docs/data-sources/module_source) (data source)

<!-- markdownlint-disable MD013 -->
## Required Inputs

The following input variables are required:

### <a name="input_location"></a> [location](#input\_location)

Description: The Azure location where the resources will be deployed.

Type: `string`

### <a name="input_name"></a> [name](#input\_name)

Description: The name of the CDN profile.

Type: `string`

### <a name="input_resource_group_name"></a> [resource\_group\_name](#input\_resource\_group\_name)

Description: The resource group where the resources will be deployed.

Type: `string`

## Optional Inputs

The following input variables are optional (have default values):

### <a name="input_cdn_endpoint_custom_domains"></a> [cdn\_endpoint\_custom\_domains](#input\_cdn\_endpoint\_custom\_domains)

Description:   Manages a map of CDN Endpoint Custom Domains. A CDN Endpoint Custom Domain is a custom domain that is associated with a CDN Endpoint.

 - `cdn_endpoint_key` - (Required) key of the endpoint defined in variable cdn\_endpoints.
 - `dns_zone` - (Required) A map of DNS Zone details for the custom domain. Each dns\_zone block supports the following: -
  - `is_azure_dns_zone` - (Required) Is the custom domain hosted on Azure DNS Zone?
  - `name` - (Required) The name of the DNS Zone for the custom domain.
  - `cname_record_name` - (Required) The name of the CNAME record to create in the DNS Zone.
  - `ttl` - (Required) The TTL of the CNAME record.
  - `tags` - (Optional) A mapping of tags to assign to the CNAME record.
  - `azure_dns_zone_resource_group_name_name` - (Optional) The name of the Azure resource group where the DNS Zone is located. This is required if the DNS Zone is in azure.
 - `name` - (Required) The name which should be used for this CDN Endpoint Custom Domain. Changing this forces a new CDN Endpoint Custom Domain to be created.
 - `cdn_managed_https` block supports the following:
  - `certificate_type` - (Required) The type of HTTPS certificate. Possible values are `Shared` and `Dedicated`.
  - `protocol_type` - (Required) The type of protocol. Possible values are `ServerNameIndication` and `IPBased`.
  - `tls_version` - (Optional) The minimum TLS protocol version that is used for HTTPS. Possible values are `TLS10` (representing TLS 1.0/1.1), `TLS12` (representing TLS 1.2) and `None` (representing no minimums). Defaults to `TLS12`.
 - `user_managed_https` block supports the following:
  - `key_vault_certificate_id` - (Optional) The ID of the Key Vault Certificate that contains the HTTPS certificate. This is deprecated in favor of `key_vault_secret_id`.
  - `key_vault_secret_id` - (Optional) The ID of the Key Vault Secret that contains the HTTPS certificate.
  - `tls_version` - (Optional) The minimum TLS protocol version that is used for HTTPS. Possible values are `TLS10` (representing TLS 1.0/1.1), `TLS12` (representing TLS 1.2) and `None` (representing no minimums). Defaults to `TLS12`.  
 Example Input:

  ```terraform
  cdn_endpoint_custom_domains = {
    cdn1 = {
      cdn_endpoint_key = "ep1"
      dns_zone = {
        is_azure_dns_zone                  = true
        name                               = data.azurerm_dns_zone.dns.name
        cname_record_name                  = "www"
        azure_dns_zone_resource_group_name = data.azurerm_dns_zone.dns.resource_group_name
      }
      name = "example-domain"
      cdn_managed_https = {
        certificate_type = "Dedicated"
        protocol_type    = "ServerNameIndication"
        tls_version      = "TLS12"
      }
    }
  }
```
  `Note:` You may face issue in destroying the CDN custom domain when running "terraform destroy" because it requires the Cname record in the DNS zone to be deleted first. In such case run the below commands (only once per subscription) before running the "terraform destroy" command :-

  ```cli
  \\run below command to register feature to bypass cname check for custom domain deletion
  az feature register --namespace Microsoft.Cdn --name BypassCnameCheckForCustomDomainDeletion

  \\run below command to check status of the registeration of the feature
  az feature list -o table --query "[?contains(name, 'Microsoft.Cdn/BypassCnameCheckForCustomDomainDeletion')].{Name:name,State:properties.state}"

  \\run below command once registeration is completed
  az provider register --namespace Microsoft.Cdn
```

Type:

```hcl
map(object({
    cdn_endpoint_key = string
    dns_zone = optional(object({
      is_azure_dns_zone                  = bool
      name                               = string
      cname_record_name                  = string
      ttl                                = number
      tags                               = optional(map(string))
      azure_dns_zone_resource_group_name = optional(string, null)
    }))
    name = string
    cdn_managed_https = optional(object({
      certificate_type = string
      protocol_type    = string
      tls_version      = optional(string, "TLS12")
    }))
    user_managed_https = optional(object({
      key_vault_certificate_id = optional(string)
      key_vault_secret_id      = optional(string)
      tls_version              = optional(string)
    }))
  }))
```

Default: `{}`

### <a name="input_cdn_endpoints"></a> [cdn\_endpoints](#input\_cdn\_endpoints)

Description:   Manages a map of CDN Endpoints. A CDN Endpoint is the entity within a CDN Profile containing configuration information regarding caching behaviours and origins.

  - `name` - (Required) The name of the CDN Endpoint. Changing this forces a new CDN Endpoint to be created.
  - `tags` - (Optional) A mapping of tags to assign to the CDN Endpoint.
  - `is_http_allowed` - (Optional) Is HTTP allowed for the CDN Endpoint? Defaults to false.
  - `is_https_allowed` - (Optional) Is HTTPS allowed for the CDN Endpoint? Defaults to true.
  - `content_types_to_compress` - (Optional) A list of content types to compress.The value for the elements should be MIME types.Defaults to `[]`.
  - `geo_filters` - (Optional) A map of geo filters to apply to the CDN Endpoint. Each geo\_filter block supports fields documented below: -
    - `relative_path` - (Required) The relative path for the geo filter. Must be "/" for Standard\_Microsoft. Must be unique across all filters. Only one allowed for Standard\_Microsoft.
    - `action` - (Required) The action to take when the filter is matched. Allowed values are `Allow` or `Block`.
    - `country_codes` - (Required) A list of two-letter country codes to match. E.g. `["US", "CA"]`.
  - `is_compression_enabled` - (Optional) Is compression enabled for the CDN Endpoint? Defaults to false.
  - `querystring_caching_behaviour` - (Optional) The query string caching behaviour for the CDN Endpoint. Allowed values are `IgnoreQueryString`, `BypassCaching`, `UseQueryString`. `NotSet` value can be used for premium verizon. Defaults to `IgnoreQueryString`.
  - `optimization_type` - (Optional) The optimization type for the CDN Endpoint. Allowed values are `DynamicSiteAcceleration`, `GeneralMediaStreaming`, `GeneralWebDelivery`, `LargeFileDownload`, `VideoOnDemandMediaStreaming`.
  - `origins` - (Required) A map of origins to associate with the CDN Endpoint. Each origins block supports fields documented below: -
    - `name` - (Required) The name of the origin.
    - `host_name` - (Required) The host name of the origin.
    - `http_port` - (Optional) The HTTP port of the origin. Defaults to 80.
    - `https_port` - (Optional) The HTTPS port of the origin. Defaults to 443.
  - `origin_host_header` - (Optional) The host header to send to the origin. Changing this forces a new CDN Endpoint to be created.
  - `origin_path` - (Optional) The path to the origin. Must start with `/` e.g. `"/media"`.
  - `probe_path` - (Optional) The path to the probe. Must start with `/` e.g. `"/foo.bar"`.
  - `global_delivery_rule` - (Optional) A global delivery rule block as defined below: -
    - `cache_expiration_action` - (Optional) A list of cache expiration action blocks as defined below: -
      - `behavior` - (Required) The behavior of the cache expiration action. Allowed values are `BypassCache`, `Override`, `SetIfMissing`.
      - `duration` - (Optional) The duration of the cache expiration action. Only allowed when behavior is `Override` or `SetIfMissing`. Format: `[d.]hh:mm:ss` e.g. `"1.10:30:00"`.
    - `cache_key_query_string_action` - (Optional) A list of cache key query string action blocks as defined below: -
      - `behavior` - (Required) The behavior of the cache key query string action. Allowed values are `Exclude`, `ExcludeAll`, `Include`, `IncludeAll`.
      - `parameters` - (Optional) The parameters of the cache key query string action. E.g. `"*"`.
    - `modify_request_header_action` - (Optional) A list of modify request header action blocks as defined below: -
      - `action` - (Required) The action of the modify request header action. Allowed values are `Append`, `Delete`, `Overwrite`.
      - `name` - (Required) The name of the modify request header action.
      - `value` - (Optional) The value of the modify request header action. Only needed if action is `Append` or `Overwrite`.
    - `modify_response_header_action` - (Optional) A list of modify response header action blocks as defined below: -
      - `action` - (Required) The action of the modify response header action. Allowed values are `Append`, `Delete`, `Overwrite`.
      - `name` - (Required) The name of the modify response header action.
      - `value` - (Optional) The value of the modify response header action. Only needed if action is `Append` or `Overwrite`.
    - `url_redirect_action` - (Optional) A list of URL redirect action blocks as defined below: -
      - `redirect_type` - (Required) The redirect type of the URL redirect action. Allowed values are `Found`, `Moved`, `PermanentRedirect`, `TemporaryRedirect`.
      - `protocol` - (Optional) The protocol of the URL redirect action. Allowed values are `MatchRequest`, `Http`, `Https`. Defaults to `Https`.
      - `hostname` - (Optional) The hostname of the URL redirect action.
      - `path` - (Optional) The path of the URL redirect action. Should begin with `/`.
      - `fragment` - (Optional) The fragment of the URL redirect action. Specifies the fragment part of the URL. This value must not start with a `#`.
      - `query_string` - (Optional) The query string of the URL redirect action. Specifies the query string part of the URL. This value must not start with a `?` or `&` and must be in `<key>=<value>` format separated by `&`.
    - `url_rewrite_action` - (Optional) A list of URL rewrite action blocks as defined below: -
      - `source_pattern` - (Required) The source pattern of the URL rewrite action. This value must start with a `/` and can't be longer than 260 characters.
      - `destination` - (Required) The destination of the URL rewrite action. This value must start with a `/` and can't be longer than 260 characters.
      - `preserve_unmatched_path` - (Optional) Specifies whether to preserve the unmatched path. Defaults to `true`.
  - `delivery_rules` - (Optional) A list of delivery rules blocks as defined below: -
    - `name` - (Required) The name of the delivery rule.
    - `order` - (Required) The order of the delivery rule.
    - `cache_expiration_action` - (Optional) A cache expiration action block as defined below: -
      - `behavior` - (Required) The behavior of the cache expiration action.
      - `duration` - (Optional) The duration of the cache expiration action.
    - `cache_key_query_string_action` - (Optional) A cache key query string action block as defined below: -
      - `behavior` - (Required) The behavior of the cache key query string action.
      - `parameters` - (Optional) The parameters of the cache key query string action.
    - `cookies_condition` - (Optional) A cookies condition block as defined below: -
      - `selector` - (Required) The selector of the cookies condition.
      - `operator` - (Required) The operator of the cookies condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the cookies condition.
      - `transforms` - (Optional) The transforms of the cookies condition.
    - `device_condition` - (Optional) A device condition block as defined below: -
      - `operator` - (Optional) The operator of the device condition. Defaults to `Equal`.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Required) The match values of the device condition.
    - `http_version_condition` - (Optional) An HTTP version condition block as defined below: -
      - `operator` - (Optional) The operator of the HTTP version condition. Defaults to `Equal`.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Required) The match values of the HTTP version condition.
    - `modify_request_header_action` - (Optional) A modify request header action block as defined below: -
      - `action` - (Required) The action of the modify request header action.
      - `name` - (Required) The name of the modify request header action.
      - `value` - (Optional) The value of the modify request
    - `modify_response_header_action` - (Optional) A modify response header action block as defined below: -
      - `action` - (Required) The action of the modify response header action.
      - `name` - (Required) The name of the modify response header action.
      - `value` - (Optional) The value of the modify response header action.
    - `post_arg_condition` - (Optional) A post argument condition block as defined below: -
      - `selector` - (Required) The selector of the post argument condition.
      - `operator` - (Required) The operator of the post argument condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the post argument condition.
      - `transforms` - (Optional) The transforms of the post argument condition.
    - `query_string_condition` - (Optional) A query string condition block as defined below: -
      - `operator` - (Required) The operator of the query string condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the query string condition.
      - `transforms` - (Optional) The transforms of the query string condition.
    - `remote_address_condition` - (Optional) A remote address condition block as defined below: -
      - `operator` - (Required) The operator of the remote address condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the remote address condition.
    - `request_body_condition` - (Optional) A request body condition block as defined below: -
      - `operator` - (Required) The operator of the request body condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the request body condition.
      - `transforms` - (Optional) The transforms of the request body condition.
    - `request_header_condition` - (Optional) A request header condition block as defined below: -
      - `selector` - (Required) The selector of the request header condition.
      - `operator` - (Required) The operator of the request header condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the request header condition.
      - `transforms` - (Optional) The transforms of the request header condition.
    - `request_method_condition` - (Optional) A request method condition block as defined below: -
      - `operator` - (Optional) The operator of the request method condition. Defaults to `Equal`.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Required) The match values of the request method condition.
    - `request_scheme_condition` - (Optional) A request scheme condition block as defined below: -
      - `operator` - (Optional) The operator of the request scheme condition. Defaults to `Equal`.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Required) The match values of the request scheme condition.
    - `request_uri_condition` - (Optional) A request URI condition block as defined below: -
      - `operator` - (Required) The operator of the request URI condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the request URI condition.
      - `transforms` - (Optional) The transforms of the request URI condition.
    - `url_file_extension_condition` - (Optional) A URL file extension condition block as defined below: -
      - `operator` - (Required) The operator of the URL file extension condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the URL file extension condition.
      - `transforms` - (Optional) The transforms of the URL file extension condition.
    - `url_file_name_condition` - (Optional) A URL file name condition block as defined below: -
      - `operator` - (Required) The operator of the URL file name condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the URL file name condition.
      - `transforms` - (Optional) The transforms of the URL file name condition.
    - `url_path_condition` - (Optional) A URL path condition block as defined below: -
      - `operator` - (Required) The operator of the URL path condition.
      - `negate_condition` - (Optional) Should the condition be negated? Defaults to `false`.
      - `match_values` - (Optional) The match values of the URL path condition.
      - `transforms` - (Optional) The transforms of the URL path condition.
    - `url_redirect_action` - (Optional) A URL redirect action block as defined below: -
      - `redirect_type` - (Required) The redirect type of the URL redirect action.
      - `protocol` - (Optional) The protocol of the URL redirect action. Defaults to `MatchRequest`.
      - `hostname` - (Optional) The hostname of the URL redirect action.
      - `path` - (Optional) The path of the URL redirect action. Should begin with `/`.
      - `fragment` - (Optional) The fragment of the URL redirect action. Specifies the fragment part of the URL. This value must not start with a `#`.
      - `query_string` - (Optional) The query string of the URL redirect action. Specifies the query string part of the URL. This value must not start with a `?` or `&` and must be in `<key>=<value>` format separated by `&`.
    - `url_rewrite_action` - (Optional) A URL rewrite action block as defined below: -
      - `source_pattern` - (Required) The source pattern of the URL rewrite action. This value must start with a `/` and can't be longer than 260 characters.
      - `destination` - (Required) The destination of the URL rewrite action. This value must start with a `/` and can't be longer than 260 characters.
      - `preserve_unmatched_path` - (Optional) Specifies whether to preserve the unmatched path. Defaults to `true`.
  - `diagnostic_setting` - (Optional) A diagnostic setting block as defined below: -
    - `name` - (Optional) The name of the diagnostic setting. One will be generated if not set, however this will not be unique if you want to create multiple diagnostic setting resources.
    - `log_categories` - (Optional) A set of log categories to send to the log analytics workspace. Defaults to `[]`.
    - `log_groups` - (Optional) A set of log groups to send to the log analytics workspace. Defaults to `["allLogs"]`.
    - `metric_categories` - (Optional) A set of metric categories to send to the log analytics workspace. Defaults to `["AllMetrics"]`.
    - `log_analytics_destination_type` - (Optional) The destination type for the diagnostic setting. Possible values are `Dedicated` and `AzureDiagnostics`. Defaults to `Dedicated`.
    - `workspace_resource_id` - (Optional) The resource ID of the log analytics workspace to send logs and metrics to.
    - `storage_account_resource_id` - (Optional) The resource ID of the storage account to send logs and metrics to.
    - `event_hub_authorization_rule_resource_id` - (Optional) The resource ID of the event hub authorization rule to send logs and metrics to.
    - `event_hub_name` - (Optional) The name of the event hub. If none is specified, the default event hub will be selected.
    - `marketplace_partner_resource_id` - (Optional) The full ARM resource ID of the Marketplace resource to which you would like to send Diagnostic LogsLogs.

  Example Input:

  ```terraform
    cdn_endpoints = {
      ep1 = {
        name                          = "endpoint-ex"
        is_http_allowed               = true
        is_https_allowed              = true
        querystring_caching_behaviour = "BypassCaching"
        is_compression_enabled        = true
        optimization_type             = "GeneralWebDelivery"
        geo_filters = { # Only one geo filter allowed for Standard_Microsoft sku
          gf1 = {
            relative_path = "/"
            action        = "Block"
            country_codes = ["AF", "GB"]
          }
        }
        content_types_to_compress = [
          "application/eot",
          "application/font",
          "application/font-sfnt",
          "application/javascript",
          "application/json",
          "application/opentype",
          "application/otf",
          "application/pkcs7-mime",
          "application/truetype",
          "application/ttf",
          "application/vnd.ms-fontobject",
          "application/xhtml+xml",
          "application/xml",
          "application/xml+rss",
          "application/x-font-opentype",
          "application/x-font-truetype",
          "application/x-font-ttf",
          "application/x-httpd-cgi",
          "application/x-javascript",
          "application/x-mpegurl",
          "application/x-opentype",
          "application/x-otf",
          "application/x-perl",
          "application/x-ttf",
          "font/eot",
          "font/ttf",
          "font/otf",
          "font/opentype",
          "image/svg+xml",
          "text/css",
          "text/csv",
          "text/html",
          "text/javascript",
          "text/js",
          "text/plain",
          "text/richtext",
          "text/tab-separated-values",
          "text/xml",
          "text/x-script",
          "text/x-component",
          "text/x-java-source",
        ]
        origin_host_header = replace(replace(azurerm_storage_account.storage.primary_blob_endpoint, "https://", ""), "/", "")
        origin_path        = "/media"
        probe_path         = "/foo.bar"
        origins = {
          og1 = { name = "origin1"
            host_name = replace(replace(azurerm_storage_account.storage.primary_blob_endpoint, "https://", ""), "/", "")
          }
        }
        diagnostic_setting = {
          name                        = "storage_diag"
          log_groups                  = ["allLogs"]
          storage_account_resource_id = azurerm_storage_account.storage.id
          marketplace_partner_resource_id          = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/{partnerResourceProvider}/{partnerResourceType}/{partnerResourceName}"
        }
      }
    }
```

Type:

```hcl
map(object({
    name                      = string
    tags                      = optional(map(any))
    is_http_allowed           = optional(bool, false)
    is_https_allowed          = optional(bool, true)
    content_types_to_compress = optional(list(string), [])

    geo_filters = optional(map(object({
      relative_path = string       # must be "/" for Standard_Microsoft. Must be unique across all filters. Only one allowed for Standard_Microsoft
      action        = string       # allowed values: Allow or Block
      country_codes = list(string) # Two letter country codes allows e.g. ["US", "CA"]
    })), {})

    is_compression_enabled        = optional(bool)
    querystring_caching_behaviour = optional(string, "IgnoreQueryString") # allowed values: IgnoreQueryString,BypassCaching ,UseQueryString,NotSet for premium verizon.
    optimization_type             = optional(string)                      # allowed values: DynamicSiteAcceleration,GeneralMediaStreaming,GeneralWebDelivery,LargeFileDownload ,VideoOnDemandMediaStreaming

    origins = map(object({
      name       = string
      host_name  = string
      http_port  = optional(number, 80)
      https_port = optional(number, 443)
    }))

    origin_host_header = optional(string)
    origin_path        = optional(string) # must start with '/' e.g. "/media"
    probe_path         = optional(string) # must start with '/' e.g. "/foo.bar"

    global_delivery_rule = optional(object({
      cache_expiration_action = optional(list(object({
        behavior = string           # Allowed Values: BypassCache, Override and SetIfMissing
        duration = optional(string) # Only allowed when behavior is Override or SetIfMissing. Format: [d.]hh:mm:ss e.g "1.10:30:00"
      })), [])
      cache_key_query_string_action = optional(list(object({
        behavior   = string           # Allowed Values: Exclude, ExcludeAll, Include and IncludeAll
        parameters = optional(string) # Documentation says it is a list but string e.g "*"
      })), [])
      modify_request_header_action = optional(list(object({
        action = string # Allowed Values: Append, Delete and Overwrite
        name   = string
        value  = optional(string) # Only needed if action = Append or Overwrite
      })), [])
      modify_response_header_action = optional(list(object({
        action = string # Allowed Values: Append, Delete and Overwrite
        name   = string
        value  = optional(string) # Only needed if action = Append or Overwrite
      })), [])
      url_redirect_action = optional(list(object({
        redirect_type = string                    # Allowed Values: Found, Moved, PermanentRedirect and TemporaryRedirect
        protocol      = optional(string, "Https") # Allowed Values: MatchRequest, Http and Https
        hostname      = optional(string)
        path          = optional(string) # Should begin with '/'
        fragment      = optional(string) # Specifies the fragment part of the URL. This value must not start with a '#'
        query_string  = optional(string) # Specifies the query string part of the URL. This value must not start with a '?' or '&' and must be in <key>=<value> format separated by '&'.
      })), [])
      url_rewrite_action = optional(list(object({
        source_pattern          = string # (Required) This value must start with a '/' and can't be longer than 260 characters.
        destination             = string # This value must start with a '/' and can't be longer than 260 characters.
        preserve_unmatched_path = optional(bool, true)
      })), [])
    }), {})

    delivery_rules = optional(list(object({
      name  = string
      order = number
      cache_expiration_action = optional(object({
        behavior = string
        duration = optional(string)
      }))
      cache_key_query_string_action = optional(object({
        behavior   = string
        parameters = optional(string)
      }))
      cookies_condition = optional(object({
        selector         = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      device_condition = optional(object({
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
        match_values     = list(string)
      }))
      http_version_condition = optional(object({
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
        match_values     = list(string)
      }))
      modify_request_header_action = optional(object({
        action = string
        name   = string
        value  = optional(string)
      }))
      modify_response_header_action = optional(object({
        action = string
        name   = string
        value  = optional(string)
      }))
      post_arg_condition = optional(object({
        selector         = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      query_string_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      remote_address_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
      }))

      request_body_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      request_header_condition = optional(object({
        selector         = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      request_method_condition = optional(object({
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
        match_values     = list(string)
      }))
      request_scheme_condition = optional(object({
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
        match_values     = list(string)
      }))
      request_uri_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      url_file_extension_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      url_file_name_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      url_path_condition = optional(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      }))
      url_redirect_action = optional(object({
        redirect_type = string
        protocol      = optional(string, "MatchRequest")
        hostname      = optional(string)
        path          = optional(string)
        fragment      = optional(string)
        query_string  = optional(string)
      }))
      url_rewrite_action = optional(object({
        source_pattern          = string
        destination             = string
        preserve_unmatched_path = optional(bool, true)
      }))
    })))
    diagnostic_setting = optional(object({
      name                                     = optional(string, null)
      log_categories                           = optional(set(string), [])
      log_groups                               = optional(set(string), [])
      metric_categories                        = optional(set(string), [])
      log_analytics_destination_type           = optional(string, "Dedicated")
      workspace_resource_id                    = optional(string, null)
      storage_account_resource_id              = optional(string, null)
      event_hub_authorization_rule_resource_id = optional(string, null)
      event_hub_name                           = optional(string, null)
      marketplace_partner_resource_id          = optional(string, null)
    }), null)
  }))
```

Default: `{}`

### <a name="input_diagnostic_settings"></a> [diagnostic\_settings](#input\_diagnostic\_settings)

Description:   Manages a map of diagnostic settings on the CDN/front door profile. The map key is deliberately arbitrary to avoid issues where map keys maybe unknown at plan time.

  - `name` - (Optional) The name of the diagnostic setting. One will be generated if not set, however this will not be unique if you want to create multiple diagnostic setting resources.
  - `log_categories` - (Optional) A set of log categories to send to the log analytics workspace. Defaults to `[]`.
  - `log_groups` - (Optional) A set of log groups to send to the log analytics workspace. Defaults to `["allLogs"]`.
  - `metric_categories` - (Optional) A set of metric categories to send to the log analytics workspace. Defaults to `["AllMetrics"]`.
  - `log_analytics_destination_type` - (Optional) The destination type for the diagnostic setting. Possible values are `Dedicated` and `AzureDiagnostics`. Defaults to `Dedicated`.
  - `workspace_resource_id` - (Optional) The resource ID of the log analytics workspace to send logs and metrics to.
  - `storage_account_resource_id` - (Optional) The resource ID of the storage account to send logs and metrics to.
  - `event_hub_authorization_rule_resource_id` - (Optional) The resource ID of the event hub authorization rule to send logs and metrics to.
  - `event_hub_name` - (Optional) The name of the event hub. If none is specified, the default event hub will be selected.
  - `marketplace_partner_resource_id` - (Optional) The full ARM resource ID of the Marketplace resource to which you would like to send Diagnostic LogsLogs.  
  Example Input:

  ```terraform
    diagnostic_settings = {
      workspaceandstorage_diag = {
        name                           = "workspaceandstorage_diag"
        metric_categories              = ["AllMetrics"]
        log_categories                 = ["FrontDoorAccessLog", "FrontDoorHealthProbeLog", "FrontDoorWebApplicationFirewallLog"]
        log_groups                     = [] #must explicitly set since log_groups defaults to ["allLogs"]
        log_analytics_destination_type = "Dedicated"
        workspace_resource_id          = azurerm_log_analytics_workspace.workspace.id
        storage_account_resource_id    = azurerm_storage_account.storage.id
        #marketplace_partner_resource_id          = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/{partnerResourceProvider}/{partnerResourceType}/{partnerResourceName}"
      }
      eventhub_diag = {
        name                                     = "eventhubforwarding"
        log_groups                               = ["allLogs", "Audit"] # you can set either log_categories or log_groups.
        metric_categories                        = ["AllMetrics"]
        event_hub_authorization_rule_resource_id = azurerm_eventhub_namespace_authorization_rule.example.id
        event_hub_name                           = azurerm_eventhub_namespace.eventhub_namespace.name
      }
    }
```

Type:

```hcl
map(object({
    name                                     = optional(string, null)
    log_categories                           = optional(set(string), [])
    log_groups                               = optional(set(string), ["allLogs"])
    metric_categories                        = optional(set(string), ["AllMetrics"])
    log_analytics_destination_type           = optional(string, "Dedicated")
    workspace_resource_id                    = optional(string, null)
    storage_account_resource_id              = optional(string, null)
    event_hub_authorization_rule_resource_id = optional(string, null)
    event_hub_name                           = optional(string, null)
    marketplace_partner_resource_id          = optional(string, null)
  }))
```

Default: `{}`

### <a name="input_enable_telemetry"></a> [enable\_telemetry](#input\_enable\_telemetry)

Description:   This variable controls whether or not telemetry is enabled for the module.  
  For more information see https://aka.ms/avm/telemetryinfo.  
  If it is set to false, then no telemetry will be collected.

Type: `bool`

Default: `true`

### <a name="input_front_door_custom_domains"></a> [front\_door\_custom\_domains](#input\_front\_door\_custom\_domains)

Description:   Manages a map of Front Door (standard/premium) Custom Domains.

  - `name` - (Required) The name which should be used for this Front Door Custom Domain.
  - `dns_zone_id` - (Optional) The ID of the Azure DNS Zone which should be used for this Front Door Custom Domain.
  - `host_name` - (Required) The host name of the domain. The host\_name field must be the FQDN of your domain.
  - `tls` - (Required) A tls block as defined below : -
    - `certificate_type` - (Optional) Defines the source of the SSL certificate. Possible values include 'CustomerCertificate' and 'ManagedCertificate'. Defaults to 'ManagedCertificate'.
    - `cdn_frontdoor_secret_key` - (Optional) Key of the Front Door Secret object. This is required when certificate\_type is 'CustomerCertificate'.  
  Example Input:

  ```terraform
  front_door_custom_domains = {
    contoso1_key = {
        name        = "contoso1"
        dns_zone_id = azurerm_dns_zone.dnszone.id
        host_name   = "contoso1.fabrikam.com"
        tls = {
          certificate_type    = "ManagedCertificate"
          cdn_frontdoor_secret_key = "Secret1_key"
        }
      }
    }
```

Type:

```hcl
map(object({
    name        = string
    dns_zone_id = optional(string, null)
    host_name   = string
    tls = object({
      certificate_type         = optional(string, "ManagedCertificate")
      cdn_frontdoor_secret_key = optional(string, null)
    })
  }))
```

Default: `{}`

### <a name="input_front_door_endpoints"></a> [front\_door\_endpoints](#input\_front\_door\_endpoints)

Description:   Manages a map of Front Door (standard/premium) Endpoints.

  - `name` - (Required) The name which should be used for this Front Door Endpoint.
  - `enabled` - (Optional) Specifies if this Front Door Endpoint is enabled? Defaults to true.
  - `tags` - (Optional) Specifies a mapping of tags which should be assigned to the Front Door Endpoint.  
  Example Input:

  ```terraform
  front_door_endpoints = {
    ep1_key = {
        name = "ep1-ex"
        enabled = true
        tags = {
          environment = "avm-demo"
        }
      }
    }
```

Type:

```hcl
map(object({
    name    = string
    enabled = optional(bool, true)
    tags    = optional(map(any))
  }))
```

Default: `{}`

### <a name="input_front_door_firewall_policies"></a> [front\_door\_firewall\_policies](#input\_front\_door\_firewall\_policies)

Description:   Manages a map of Front Door (standard/premium) Firewall Policies.

  - `name` - (Required) The name which should be used for this Front Door Security Policy. Possible values must not be an empty string.
  - `resource_group_name` - (Required) The name of the resource group. Changing this forces a new resource to be created.
  - `sku_name` - (Required) The sku's pricing tier for this Front Door Firewall Policy. Possible values include 'Standard\_AzureFrontDoor' or 'Premium\_AzureFrontDoor'.
  - `enabled` - (Optional) Is the Front Door Firewall Policy enabled? Defaults to true.
  - `mode` - (Required) The Front Door Firewall Policy mode. Possible values are 'Detection', 'Prevention'.
  - `request_body_check_enabled` - (Optional) Should policy managed rules inspect the request body content? Defaults to true.
  - `redirect_url` - (Optional) If action type is redirect, this field represents redirect URL for the client.
  - `custom_block_response_status_code` - (Optional) If a custom\_rule block's action type is block, this is the response status code. Possible values are 200, 403, 405, 406, or 429.
  - `custom_block_response_body` - (Optional) If a custom\_rule block's action type is block, this is the response body. The body must be specified in base64 encoding.
  - `custom_rules` - (Optional) One or more custom\_rule blocks as defined below.
    - `name` - (Required) Gets name of the resource that is unique within a policy. This name can be used to access the resource.
    - `action` - (Required) The action to perform when the rule is matched. Possible values are 'Allow', 'Block', 'Log', or 'Redirect'.
    - `enabled` - (Optional) Is the rule is enabled or disabled? Defaults to true.
    - `priority` - (Optional) The priority of the rule. Rules with a lower value will be evaluated before rules with a higher value. Defaults to 1.
    - `type` - (Required) The type of rule. Possible values are MatchRule or RateLimitRule.
    - `rate_limit_duration_in_minutes` - (Optional) The rate limit duration in minutes. Defaults to 1.
    - `rate_limit_threshold` - (Optional) The rate limit threshold. Defaults to 10.
    - `match_conditions` - (Optional) One or more match\_condition block defined below. Can support up to 10 match\_condition blocks.
      - `match_variable` - (Required) The request variable to compare with. Possible values are Cookies, PostArgs, QueryString, RemoteAddr, RequestBody, RequestHeader, RequestMethod, RequestUri, or SocketAddr.
      - `match_values` - (Required) Up to 600 possible values to match. Limit is in total across all match\_condition blocks and match\_values arguments. String value itself can be up to 256 characters in length.
      - `operator` - (Required) Comparison type to use for matching with the variable value. Possible values are Any, BeginsWith, Contains, EndsWith, Equal, GeoMatch, GreaterThan, GreaterThanOrEqual, IPMatch, LessThan, LessThanOrEqual or RegEx.
      - `selector` - (Optional) Match against a specific key if the match\_variable is QueryString, PostArgs, RequestHeader or Cookies
      - `negation_condition` - (Optional) Should the result of the condition be negated.
      - `transforms` - (Optional) Up to 5 transforms to apply. Possible values are Lowercase, RemoveNulls, Trim, Uppercase, URLDecode or URLEncode.
  - `managed_rules` -  (Optional) One or more managed\_rule blocks as defined below.
    - `type` - (Required) The name of the managed rule to use with this resource. Possible values include DefaultRuleSet, Microsoft\_DefaultRuleSet, BotProtection or Microsoft\_BotManagerRuleSet.
    - `version` - (Required) The version of the managed rule to use with this resource. Possible values depends on which DRS type you are using, for the DefaultRuleSet type the possible values include 1.0 or preview-0.1. For Microsoft\_DefaultRuleSet the possible values include 1.1, 2.0 or 2.1. For BotProtection the value must be preview-0.1 and for Microsoft\_BotManagerRuleSet the value must be 1.0.
    - `action` - (Required) The action to perform for all DRS rules when the managed rule is matched or when the anomaly score is 5 or greater depending on which version of the DRS you are using. Possible values include Allow, Log, Block, and Redirect.
    - `exclusion` - (Optional) One or more exclusion blocks as defined below: -
      - `match_variable` - (Required) The variable type to be excluded. Possible values are QueryStringArgNames, RequestBodyPostArgNames, RequestCookieNames, RequestHeaderNames, RequestBodyJsonArgNames.
      - `operator` - (Required) Comparison operator to apply to the selector when specifying which elements in the collection this exclusion applies to. Possible values are: Equals, Contains, StartsWith, EndsWith, EqualsAny.
      - `selector` - (Required) Selector for the value in the match\_variable attribute this exclusion applies to.
    - `overrides` - (Optional) One or more override blocks as defined below: -
      - `rule_group_name` - (Required) The managed rule group to override.
      - `exclusions` - (Optional) One or more exclusion blocks as defined below: -
        - `match_variable` - (Required) The variable type to be excluded. Possible values are QueryStringArgNames, RequestBodyPostArgNames, RequestCookieNames, RequestHeaderNames, RequestBodyJsonArgNames.
        - `operator` - (Required) Comparison operator to apply to the selector when specifying which elements in the collection this exclusion applies to. Possible values are: Equals, Contains, StartsWith, EndsWith, EqualsAny.
        - `selector` - (Required) Selector for the value in the match\_variable attribute this exclusion applies to.
      - `rules` - (Optional) One or more rule blocks as defined below. If none are specified, all of the rules in the group will be disabled: -
        - `rule_id` - (Required) Identifier for the managed rule.
        - `action` - (Required) The action to be applied when the managed rule matches or when the anomaly score is 5 or greater. Possible values for DRS 1.1 and below are Allow, Log, Block, and Redirect. For DRS 2.0 and above the possible values are Log or AnomalyScoring.
        - `enabled` - (Optional) Is the managed rule override enabled or disabled. Defaults to false.
        - `exclusions` - (Optional) One or more exclusion blocks as defined below: -
          - `match_variable` - (Required) The variable type to be excluded. Possible values are QueryStringArgNames, RequestBodyPostArgNames, RequestCookieNames, RequestHeaderNames, RequestBodyJsonArgNames.
          - `operator` - (Required) Comparison operator to apply to the selector when specifying which elements in the collection this exclusion applies to. Possible values are: Equals, Contains, StartsWith, EndsWith, EqualsAny.
          - `selector` - (Required) Selector for the value in the match\_variable attribute this exclusion applies to.
  - `tags` - (Optional) A mapping of tags to assign to the Front Door Firewall Policy.
  /*  
  Example Input:

  ```terraform
  front_door_firewall_policies = {
      fd_waf1_key = {
      name                              = "examplecdnfdwafpolicy1"
      resource_group_name               = azurerm_resource_group.this.name
      sku_name                          = "Premium_AzureFrontDoor" # Ensure SKU_name for WAF is similar to SKU_name for front door profile.
      enabled                           = true
      mode                              = "Prevention"
      redirect_url                      = "https://www.contoso.com"
      custom_block_response_status_code = 405
      custom_block_response_body        = "PGh0bWw+CjxoZWFkZXI+PHRpdGxlPkhlbGxvPC90aXRsZT48L2hlYWRlcj4KPGJvZHk+CkhlbGxvIHdvcmxkCjwvYm9keT4KPC9odG1sPg=="

      custom_rules = {
        cr1 = {
          name                           = "Rule1"
          enabled                        = true
          priority                       = 1
          rate_limit_duration_in_minutes = 1
          rate_limit_threshold           = 10
          type                           = "MatchRule"
          action                         = "Block"
          match_conditions = {
            m1 = {
              match_variable     = "RemoteAddr"
              operator           = "IPMatch"
              negation_condition = false
              match_values       = ["10.0.1.0/24", "10.0.0.0/24"]
            }
          }
        }

        cr2 = {
          name                           = "Rule2"
          enabled                        = true
          priority                       = 2
          rate_limit_duration_in_minutes = 1
          rate_limit_threshold           = 10
          type                           = "MatchRule"
          action                         = "Block"
          match_conditions = {
            match_condition1 = {
              match_variable     = "RemoteAddr"
              operator           = "IPMatch"
              negation_condition = false
              match_values       = ["192.168.1.0/24"]
            }

            match_condition2 = {
              match_variable     = "RequestHeader"
              selector           = "UserAgent"
              operator           = "Contains"
              negation_condition = false
              match_values       = ["windows"]
              transforms         = ["Lowercase", "Trim"]
            }
          }
        }
      }
      managed_rules = {
        mr1 = {
          type    = "Microsoft_DefaultRuleSet"
          version = "2.1"
          action  = "Log"
          exclusions = {
            exclusion1 = {
              match_variable = "QueryStringArgNames"
              operator       = "Equals"
              selector       = "not_suspicious"
            }
          }
          overrides = {
            override1 = {
              rule_group_name = "PHP"
              rule = {
                rule1 = {
                  rule_id = "933100"
                  enabled = false
                  action  = "Log"
                }
              }
            }
            override2 = {
              rule_group_name = "SQLI"
              exclusions = {
                exclusion1 = {
                  match_variable = "QueryStringArgNames"
                  operator       = "Equals"
                  selector       = "really_not_suspicious"
                }
              }
              rules = {
                rule1 = {
                  rule_id = "942200"
                  action  = "Log"
                  exclusions = {
                    exclusion1 = {
                      match_variable = "QueryStringArgNames"
                      operator       = "Equals"
                      selector       = "innocent"
                    }
                  }
                }
              }
            }
          }
        }

        mr2 = {
          type    = "Microsoft_BotManagerRuleSet"
          version = "1.0"
          action  = "Log"
        }
      }
    }
  }
```

Type:

```hcl
map(object({
    name                              = string
    resource_group_name               = string
    sku_name                          = string
    enabled                           = optional(bool, true)
    mode                              = string
    request_body_check_enabled        = optional(bool, true)
    redirect_url                      = optional(string)
    custom_block_response_status_code = optional(number)
    custom_block_response_body        = optional(string)
    custom_rules = optional(map(object({
      name                           = string
      enabled                        = optional(bool, true)
      priority                       = optional(number, 1)
      rate_limit_duration_in_minutes = optional(number, 1)
      rate_limit_threshold           = optional(number, 10)
      type                           = string
      action                         = string
      match_conditions = map(object({
        match_variable     = string
        operator           = string
        negation_condition = optional(bool)
        match_values       = list(string)
        selector           = optional(string)
        transforms         = optional(list(string))
      }))
    })), {})
    managed_rules = optional(map(object({
      type    = string
      version = string
      action  = string
      exclusions = optional(map(object({
        match_variable = string
        operator       = string
        selector       = optional(string)
      })), {})
      overrides = optional(map(object({
        rule_group_name = string
        exclusions = optional(map(object({
          match_variable = string
          operator       = string
          selector       = optional(string)
        })), {})
        rules = optional(map(object({
          rule_id = string
          action  = string
          enabled = optional(bool, false)
          exclusions = optional(map(object({
            match_variable = string
            operator       = string
            selector       = optional(string)
          })), {})
        })), {})
      })), {})
    })), {})
    tags = optional(map(any))
  }))
```

Default: `{}`

### <a name="input_front_door_origin_groups"></a> [front\_door\_origin\_groups](#input\_front\_door\_origin\_groups)

Description:   Manages a map of Front Door (standard/premium) Origin groups.

  - `name` - (Required) The name which should be used for this Front Door Origin Group.
  - `load_balancing` - (Required) A load\_balancing block as defined below:-
      - `additional_latency_in_milliseconds` - (Optional) Specifies the additional latency in milliseconds for probes to fall into the lowest latency bucket. Possible values are between 0 and 1000 milliseconds (inclusive). Defaults to 50
      - `sample_size` - (Optional) Specifies the number of samples to consider for load balancing decisions. Possible values are between 0 and 255 (inclusive). Defaults to 4.
      - `successful_samples_required` - (Optional) Specifies the number of samples within the sample period that must succeed. Possible values are between 0 and 255 (inclusive). Defaults to 3.
  - `health_probe` - (Optional) A health\_probe block as defined below:-
      - `protocol` - (Required) Specifies the protocol to use for health probe. Possible values are Http and Https.
      - `interval_in_seconds` - (Required) Specifies the number of seconds between health probes. Possible values are between 5 and 31536000 seconds (inclusive).
      - `request_type` - (Optional) Specifies the type of health probe request that is made. Possible values are GET and HEAD. Defaults to HEAD.
      - `path` - (Optional) Specifies the path relative to the origin that is used to determine the health of the origin. Defaults to /.  
  Example Input:

  ```terraform
  front_door_origin_groups = {
    og1_key = {
      name = "og1"
      health_probe = {
        hp1 = {
          interval_in_seconds = 240
          path                = "/healthProbe"
          protocol            = "Https"
          request_type        = "HEAD"
        }
      }
      load_balancing = {
        lb1 = {
          additional_latency_in_milliseconds = 0
          sample_size                        = 16
          successful_samples_required        = 3
        }
      }
    }
  }
```

Type:

```hcl
map(object({
    name = string
    health_probe = optional(map(object({
      interval_in_seconds = number
      path                = optional(string, "/")
      protocol            = string
      request_type        = optional(string, "HEAD")
    })), {})
    load_balancing = map(object({
      additional_latency_in_milliseconds = optional(number, 50)
      sample_size                        = optional(number, 4)
      successful_samples_required        = optional(number, 3)
    }))
  }))
```

Default: `{}`

### <a name="input_front_door_origins"></a> [front\_door\_origins](#input\_front\_door\_origins)

Description:   Manages a map of Front Door (standard/premium) Origins.

  - `name` - (Required) The name which should be used for this Front Door Origin.
  - `origin_group_key` - (Required) The key of the origin group to which this origin belongs.
  - `host_name` - (Required) The IPv4 address, IPv6 address or Domain name of the Origin.
  - `certificate_name_check_enabled` - (Required) Specifies whether certificate name checks are enabled for this origin.
  - `enabled` - (Optional) Should the origin be enabled? Possible values are true or false. Defaults to true.
  - `http_port` - (Optional) The value of the HTTP port. Must be between 1 and 65535. Defaults to 80
  - `https_port` - (Optional) The value of the HTTPS port. Must be between 1 and 65535. Defaults to 443.
  - `origin_host_header` - (Optional) The host header value (an IPv4 address, IPv6 address or Domain name) which is sent to the origin with each request. If unspecified the hostname from the request will be used.
  - `priority` - (Optional) Priority of origin in given origin group for load balancing. Higher priorities will not be used for load balancing if any lower priority origin is healthy. Must be between 1 and 5 (inclusive). Defaults to 1.
  - `weight` - (Optional) The weight of the origin in a given origin group for load balancing. Must be between 1 and 1000. Defaults to 500.
  - `private_link` - (Optional) A private\_link block as defined below:-
      - `request_message` - (Optional) Specifies the request message that will be submitted to the private\_link\_target\_id when requesting the private link endpoint connection. Values must be between 1 and 140 characters in length. Defaults to Access request for CDN FrontDoor Private Link Origin.
      - `target_type` - (Optional) Specifies the type of target for this Private Link Endpoint. Possible values are `blob`, `blob_secondary`, `web`, `sites`, `Gateway`, `managedEnvironments` and `web_secondary`.
      - `location` - (Required) Specifies the location where the Private Link resource should exist. Changing this forces a new resource to be created.
      - `private_link_target_id` - (Required) Specifies the ID of the Private Link resource to connect to.

  Example Input:

  ```terraform
  front_door_origins = {
      origin1_key = {
        name                           = "origin1"
        origin_group_key               = "og1_key"
        enabled                        = true
        certificate_name_check_enabled = true
        host_name                      = replace(replace(azurerm_storage_account.storage.primary_blob_endpoint, "https://", ""), "/", "")
        http_port                      = 80
        https_port                     = 443
        host_header                    = replace(replace(azurerm_storage_account.storage.primary_blob_endpoint, "https://", ""), "/", "")
        priority                       = 1
        weight                         = 1
        private_link = {
          pl = {
            request_message        = "Please approve this private link connection"
            target_type            = "blob"
            location               = azurerm_storage_account.storage.location
            private_link_target_id = azurerm_storage_account.storage.id
          }
        }
      }
    }
```

Type:

```hcl
map(object({
    name                           = string
    origin_group_key               = string
    host_name                      = string
    certificate_name_check_enabled = string
    enabled                        = optional(bool, true)
    http_port                      = optional(number, 80)
    https_port                     = optional(number, 443)
    host_header                    = optional(string, null)
    priority                       = optional(number, 1)
    weight                         = optional(number, 500)
    private_link = optional(map(object({
      request_message        = string
      target_type            = optional(string, null)
      location               = string
      private_link_target_id = string
    })), null)
  }))
```

Default: `{}`

### <a name="input_front_door_routes"></a> [front\_door\_routes](#input\_front\_door\_routes)

Description:   Manages a map of Front Door (standard/premium) Routes.

  - `name` - (Required) The name which should be used for this Front Door Route. Valid values must begin with a letter or number, end with a letter or number and may only contain letters, numbers and hyphens with a maximum length of 90 characters.
  - `origin_group_key` - (Required) The key of the origin group to associate the route with.
  - `origin_keys` - (Required) The list of the keys of the origins to associate the route with.
  - `endpoint_key` - (Required) The key of the endpoint to associate the route with.
  - `forwarding_protocol` - (Optional) The Protocol that will be use when forwarding traffic to backends. Possible values are 'HttpOnly', 'HttpsOnly' or 'MatchRequest'. Defaults to 'MatchRequest'.
  - `patterns_to_match` - (Required) The route patterns of the rule.
  - `supported_protocols` - (Required) One or more Protocols supported by this Front Door Route. Possible values are 'Http' or 'Https'.
  - `https_redirect_enabled` - (Optional) Automatically redirect HTTP traffic to HTTPS traffic? Possible values are true or false. Defaults to true.
  - `link_to_default_domain` - (Optional) Should this Front Door Route be linked to the default endpoint? Possible values include true or false. Defaults to true.
  - `custom_domain_keys` - (Optional) The list of the keys of the custom domains to associate the route with.
  - `enabled` - (Optional) Should the route be enabled? Possible values are true or false. Defaults to true.
  - `rule_set_names` - (Optional) The list of the names of the rule sets to associate the route with.
  - `cdn_frontdoor_origin_path` - (Optional) The path to the origin. Defaults to null.
  - `cache` - (Optional) A cache block as defined below:-
      - `query_string_caching_behavior` - (Optional) Defines how the Front Door Route will cache requests that include query strings. Possible values include 'IgnoreQueryString', 'IgnoreSpecifiedQueryStrings', 'IncludeSpecifiedQueryStrings' or 'UseQueryString'. Defaults to 'IgnoreQueryString'.
      - `query_strings` - (Optional) Query strings to include or ignore.
      - `compression_enabled` - (Optional) Is content compression enabled? Possible values are true or false. Defaults to false.
      - `content_types_to_compress` - (Optional) A list of one or more Content types (formerly known as MIME types) to compress. Possible values include 'application/eot', 'application/font', 'application/font-sfnt', 'application/javascript', 'application/json', 'application/opentype', 'application/otf', 'application/pkcs7-mime', 'application/truetype', 'application/ttf', 'application/vnd.ms-fontobject', 'application/xhtml+xml', 'application/xml', 'application/xml+rss', 'application/x-font-opentype', 'application/x-font-truetype', 'application/x-font-ttf', 'application/x-httpd-cgi', 'application/x-mpegurl', 'application/x-opentype', 'application/x-otf', 'application/x-perl', 'application/x-ttf', 'application/x-javascript', 'font/eot', 'font/ttf', 'font/otf', 'font/opentype', 'image/svg+xml', 'text/css', 'text/csv', 'text/html', 'text/javascript', 'text/js', 'text/plain', 'text/richtext', 'text/tab-separated-values', 'text/xml', 'text/x-script', 'text/x-component' or 'text/x-java-source'.  
  Example Input:

  ```terraform
  front_door_routes = {
    route1_key = {
      name                   = "route1"
      endpoint_key           = "ep1_key"
      origin_group_key       = "og1_key"
      origin_keys            = ["origin1_key"]
      https_redirect_enabled = true
      custom_domain_keys     = ["cd1_key"]
      patterns_to_match      = ["/*"]
      supported_protocols    = ["Http", "Https"]
      rule_set_names         = ["ruleset1"]
      cache = {
        cache1 = {
          query_string_caching_behavior = "IgnoreSpecifiedQueryStrings"
          query_strings                 = ["account", "settings"]
          compression_enabled           = true
          content_types_to_compress     = ["text/html", "text/javascript", "text/xml"]
        }
      }
    }
  }
```

Type:

```hcl
map(object({
    name                      = string
    origin_group_key          = string
    origin_keys               = list(string)
    endpoint_key              = string
    forwarding_protocol       = optional(string, "HttpsOnly")
    supported_protocols       = list(string)
    patterns_to_match         = list(string)
    link_to_default_domain    = optional(bool, true)
    https_redirect_enabled    = optional(bool, true)
    custom_domain_keys        = optional(list(string), [])
    enabled                   = optional(bool, true)
    rule_set_names            = optional(list(string))
    cdn_frontdoor_origin_path = optional(string, null)
    cache = optional(map(object({
      query_string_caching_behavior = optional(string, "IgnoreQueryString")
      query_strings                 = optional(list(string))
      compression_enabled           = optional(bool, false)
      content_types_to_compress     = optional(list(string))
    })), {})
  }))
```

Default: `{}`

### <a name="input_front_door_rule_sets"></a> [front\_door\_rule\_sets](#input\_front\_door\_rule\_sets)

Description:   Manages Front Door (standard/premium) Rule Sets.. The following properties can be specified:
  - `name` - (Required) The name which should be used for this Front Door Rule Set.

Type: `set(string)`

Default: `[]`

### <a name="input_front_door_rules"></a> [front\_door\_rules](#input\_front\_door\_rules)

Description:   Manages a map of Front Door (standard/premium) Rules. The following properties can be specified:

  - `name` - (Required) The name which should be used for this Front Door Rule.
  - `order` - (Required) The order in which the rule should be applied. The order value should be sequential and begin at 1(e.g. 1, 2, 3…). A Front Door Rule with a lesser order value will be applied before a rule with a greater order value.
  - `origin_group_key` - (Required) The origin group key to associate the rule with.
  - `rule_set_name` - (Required) The name of the rule set to associate the rule with.
  - `behavior_on_match` - (Optional) The behavior when a rule is matched. Possible values are 'Continue' or 'Stop'. Defaults to 'Continue'.
  - `actions` - (Required) An actions block as defined below:-
    - `url_rewrite_actions` - (Optional) A url\_rewrite\_actions block as defined below:-
      - `source_pattern` - (Required) The source pattern to match. For example, to match all URL paths use a forward slash "/" as the source pattern value.
      - `destination` - (Required) The destination to rewrite to. The destination path overwrites the source pattern.
      - `preserve_unmatched_path` - (Optional) Should the unmatched path be preserved? Possible values are true or false. Defaults to false.
    - `url_redirect_actions` - (Optional) A url\_redirect\_actions block as defined below:-
      - `redirect_type` - (Required) The type of redirect. Possible values are 'Moved', 'Found', 'TemporaryRedirect', 'PermanentRedirect' or 'SeeOther'.
      - `destination_hostname` - (Required) The destination hostname to redirect to.The value must be a string between 0 and 2048 characters in length, leave blank to preserve the incoming host.
      - `redirect_protocol` - (Optional) The protocol to use for the redirect. Possible values are 'Http' ,'Https' or 'MatchRequest'. Defaults to 'Https'.
      - `destination_path` - (Optional) The destination path to redirect to. Defaults to "". The value must be a string and include the leading /, leave blank to preserve the incoming path.
      - `query_string` - (Optional) The query string to use for the redirect. The value must be in the <key>=<value> or <key>={action\_server\_variable} format and must not include the leading ?, leave blank to preserve the incoming query string. Maximum allowed length for this field is 2048 characters. Defaults to "".
      - `destination_fragment` - (Optional) The destination fragment to use for the redirect. The value must be a string between 0 and 1024 characters in length, leave blank to preserve the incoming fragment. Defaults to "".
    - `route_configuration_override_actions` - (Optional) A route\_configuration\_override\_actions block as defined below:-
      - `set_origin_groupid` - (Required) Should the origin group ID be set? Possible values are true or false.
      - `cache_duration` - (Optional) The cache duration. Must be in the format d.HH:MM:SS (365.23:59:59).  If the desired maximum cache duration is less than 1 day then the maximum cache duration should be specified in the HH:MM:SS format(e.g. 23:59:59).
      - `forwarding_protocol` - (Optional) The forwarding protocol. Possible values are 'HttpOnly', 'HttpsOnly' or 'MatchRequest'. Defaults to 'HttpsOnly'.
      - `query_string_caching_behavior` - (Optional) The query string caching behavior. Possible values are 'IgnoreQueryString', 'IgnoreSpecifiedQueryStrings', 'IncludeSpecifiedQueryStrings' or 'UseQueryString'.
      - `query_string_parameters` - (Optional) The query string parameters to use.
      - `compression_enabled` - (Optional) Is compression enabled? Possible values are true or false. Defaults to false.
      - `cache_behavior` - (Optional) The cache behavior. Possible values include 'HonorOrigin', 'OverrideAlways', 'OverrideIfOriginMissing' or 'Disabled'.
    - `response_header_actions` - (Optional) A response\_header\_actions block as defined below:-
      - `header_action` - (Required) The header action to perform on the specified 'header\_name'. Possible values are 'Append', 'Delete' or 'Overwrite'.
      - `header_name` - (Required) The name of the header to modify.
      - `value` - (Optional) The value to set the header to. The value is required if the header\_action is set to 'Append' or 'Overwrite'.
    - `request_header_actions` - (Optional) A request\_header\_actions block as defined below:-
      - `header_action` - (Required) The header action to perform on the specified 'header\_name'. Possible values are 'Append', 'Delete' or 'Overwrite'.
      - `header_name` - (Required) The name of the header to modify.
      - `value` - (Optional) The value to set the header to. The value is required if the header\_action is set to 'Append' or 'Overwrite'.
  - `conditions` - (Optional) A conditions block as defined below:-
    - `remote_address_conditions` - (Optional) A remote\_address\_conditions block as defined below:-
      - `operator` - (Optional) The operator to use when matching the remote address. Possible values are 'Any', 'IPMatch' or 'GeoMatch'. Use the 'negate\_condition' to specify Not 'GeoMatch' or Not 'IPMatch'. Defaults to 'IPMatch'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) The values to match against. For the IP Match or IP Not Match operators: specify one or more IP address ranges. If multiple IP address ranges are specified, they're evaluated using OR logic. For the Geo Match or Geo Not Match operators: specify one or more locations using their country code.
    - `request_method_conditions` - (Optional) A request\_method\_conditions block as defined below:-
      - `match_values` - (Required) The values to match against. Possible values include 'GET', 'POST', 'PUT', 'DELETE', 'HEAD', 'OPTIONS' or 'TRACE'. If multiple values are specified, they're evaluated using OR logic.
      - `operator` - (Optional) The operator to use when matching the request method. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
    - `query_string_conditions` - (Optional) A query\_string\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the query string. Possible values are 'BeginsWith', 'Contains', 'EndsWith', 'Equal' or 'LessThan'. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `post_args_conditions` - (Optional) A post\_args\_conditions block as defined below:-
      - `post_args_name` - (Required) The name of the post args to match against.
      - `operator` - (Required) The operator to use when matching the post args. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `request_uri_conditions` - (Optional) A request\_uri\_conditions block: -
      - `operator` - (Required) The operator to use when matching the request URI. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `request_header_conditions` - (Optional) A request\_header\_conditions block as defined below:-
      - `header_name` - (Required) The name of the header to match against.
      - `operator` - (Required) The operator to use when matching the request header. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `request_body_conditions` - (Optional) A request\_body\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the request body. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `match_values` - (Required) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `request_scheme_conditions` - (Optional) A request\_scheme\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the request scheme. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) The requests protocol to match. Possible values include 'HTTP' or 'HTTPS'.
    - `url_path_conditions` - (Optional) A url\_path\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the URL path. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `url_file_extension_conditions` - (Optional) A url\_file\_extension\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the URL file extension. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Required) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `url_filename_conditions` - (Optional) A url\_filename\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the URL filename. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `http_version_conditions` - (Optional) A http\_version\_conditions block as defined below:-
      - `operator` - (Optional) The operator to use when matching the HTTP version. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Required) What HTTP version should this condition match? Possible values 2.0, 1.1, 1.0 or 0.9.
    - `cookies_conditions` - (Optional) A cookies\_conditions block as defined below:-
      - `cookie_name` - (Required) The name of the cookie to match against.
      - `operator` - (Required) The operator to use when matching the cookie. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
    - `is_device_conditions` - (Optional) A is\_device\_conditions block as defined below:-
      - `operator` - (Optional) The operator to use when matching the device. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) Which device should this rule match on? Possible values 'Mobile' or 'Desktop'.
    - `socket_address_conditions` - (Optional) A socket\_address\_conditions block as defined below:-
      - `operator` - (Optional) The operator to use when matching the socket address. Possible values are 'Any' or 'IPMatch' . Use the 'negate\_condition' to specify Not 'IPMatch'. Defaults to 'IPMatch'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) Specify one or more IP address ranges. If multiple IP address ranges are specified, they're evaluated using OR logic.
    - `client_port_conditions` - (Optional) A client\_port\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the client port. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. If multiple values are specified, they're evaluated using OR logic.
    - `server_port_conditions` - (Optional) A server\_port\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the server port. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
      - `match_values` - (Optional) One or more string or integer values(e.g. "1") representing the value of the POST argument to match. Possible values include '80' or '443'. If multiple values are specified, they're evaluated using OR logic.
    - `host_name_conditions` - (Optional) A host\_name\_conditions block as defined below:-
      - `operator` - (Required) The operator to use when matching the host name. Possible values are 'Any', 'BeginsWith', 'Contains', 'EndsWith', 'Equal', 'LessThan', 'LessThanOrEqual', 'GreaterThan', 'greaterThanOrEqual' or 'RegEx'.
      - `match_values` - (Optional) A list of one or more string values representing the value of the request hostname to match. If multiple values are specified, they're evaluated using OR logic.
      - `transforms` - (Optional) The transforms to apply to the match values. Possible values include 'Lowercase', 'RemoveNulls', 'Trim', 'Uppercase', 'UrlDecode' or 'UrlEncode'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.
    - `ssl_protocol_conditions` - (Optional) A ssl\_protocol\_conditions block as defined below:-
      - `match_values` - (Required) The values to match against. Possible values include 'TLSv1', 'TLSv1.1' and 'TLSv1.2'.  'TLSv1.3' support yet to be included in terraform.
      - `operator` - (Optional) The operator to use when matching the SSL protocol. Defaults to 'Equal'.
      - `negate_condition` - (Optional) Should the condition be negated? Possible values are true or false. Defaults to false.

  Example Input:

  ```terraform
  front_door_rules = {
    rule1_key = {
      name              = "examplerule1"
      order             = 1
      behavior_on_match = "Continue"
      rule_set_name     = "ruleset1"
      origin_group_key  = "og1_key"
      actions = {

        url_rewrite_actions = [{
          source_pattern          = "/"
          destination             = "/index3.html"
          preserve_unmatched_path = false
        }]
        route_configuration_override_actions = [{
          set_origin_groupid            = true
          forwarding_protocol           = "HttpsOnly"
          query_string_caching_behavior = "IncludeSpecifiedQueryStrings"
          query_string_parameters       = ["foo", "clientIp={client_ip}"]
          compression_enabled           = true
          cache_behavior                = "OverrideIfOriginMissing"
          cache_duration                = "365.23:59:59"
        }]
        response_header_actions = [{
          header_action = "Append"
          header_name   = "headername"
          value         = "/abc"
        }]
        request_header_actions = [{
          header_action = "Append"
          header_name   = "headername"
          value         = "/abc"
        }]
      }

      conditions = {
        remote_address_conditions = [{
          operator         = "IPMatch"
          negate_condition = false
          match_values     = ["10.0.0.0/23"]
        }]

        query_string_conditions = [{
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["Query1", "Query2"]
          transforms       = ["Uppercase"]
        }]

        request_header_conditions = [{
          header_name      = "headername"
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["Header1", "Header2"]
          transforms       = ["Uppercase"]
        }]

        request_body_conditions = [{
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["Body1", "Body2"]
          transforms       = ["Uppercase"]
        }]

        request_scheme_conditions = [{ #request protocol
          negate_condition = false
          operator         = "Equal"
          match_values     = ["HTTP"]
        }]

        url_path_conditions = [{
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["UrlPath1", "UrlPath2"]
          transforms       = ["Uppercase"]
        }]

        url_file_extension_conditions = [{
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["ext1", "ext2"]
          transforms       = ["Uppercase"]
        }]

        url_filename_conditions = [{
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["filename1", "filename2"]
          transforms       = ["Uppercase"]
        }]

        http_version_conditions = [{
          negate_condition = false
          operator         = "Equal"
          match_values     = ["2.0"]
        }]

        cookies_conditions = [{
          cookie_name      = "cookie"
          negate_condition = false
          operator         = "BeginsWith"
          match_values     = ["cookie1", "cookie2"]
          transforms       = ["Uppercase"]
        }]
      }
    }
  }
```

Type:

```hcl
map(object({
    name              = string
    order             = number
    origin_group_key  = string
    rule_set_name     = string
    behavior_on_match = optional(string, "Continue")

    actions = object({
      url_rewrite_actions = optional(list(object({
        source_pattern          = string
        destination             = string
        preserve_unmatched_path = optional(bool, false)
      })), [])
      url_redirect_actions = optional(list(object({
        redirect_type        = string
        destination_hostname = string
        redirect_protocol    = optional(string, "Https")
        destination_path     = optional(string, "")
        query_string         = optional(string, "")
        destination_fragment = optional(string, "")
      })), [])
      route_configuration_override_actions = optional(list(object({
        set_origin_groupid            = bool
        cache_duration                = optional(string) # d.HH:MM:SS (365.23:59:59)
        forwarding_protocol           = optional(string, "HttpsOnly")
        query_string_caching_behavior = optional(string)
        query_string_parameters       = optional(list(string))
        compression_enabled           = optional(bool, false)
        cache_behavior                = optional(string)
      })), [])
      request_header_actions = optional(list(object({
        header_action = string
        header_name   = string
        value         = optional(string)
      })), [])
      response_header_actions = optional(list(object({
        header_action = string
        header_name   = string
        value         = optional(string)
      })), [])
    })
    conditions = optional(object({
      remote_address_conditions = optional(list(object({
        operator         = optional(string, "IPMatch")
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
      })), [])
      request_method_conditions = optional(list(object({
        match_values     = list(string)
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
      })), [])
      query_string_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      post_args_conditions = optional(list(object({
        post_args_name   = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      request_uri_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      request_header_conditions = optional(list(object({
        header_name      = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      request_body_conditions = optional(list(object({
        operator         = string
        match_values     = list(string)
        negate_condition = optional(bool, false)
        transforms       = optional(list(string))
      })), [])
      request_scheme_conditions = optional(list(object({
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
      })), [])
      url_path_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      url_file_extension_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = list(string)
        transforms       = optional(list(string))
      })), [])
      url_filename_conditions = optional(list(object({
        operator         = string
        match_values     = optional(list(string))
        negate_condition = optional(bool, false)
        transforms       = optional(list(string))
      })), [])
      http_version_conditions = optional(list(object({
        operator         = optional(string, "Equal")
        match_values     = list(string)
        negate_condition = optional(bool, false)
      })), [])
      cookies_conditions = optional(list(object({
        cookie_name      = string
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
        transforms       = optional(list(string))
      })), [])
      is_device_conditions = optional(list(object({
        operator         = optional(string)
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
      })), [])
      socket_address_conditions = optional(list(object({
        operator         = optional(string, "IPMatch")
        negate_condition = optional(bool, false)
        match_values     = optional(list(string))
      })), [])
      client_port_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = optional(list(number))
      })), [])
      server_port_conditions = optional(list(object({
        operator         = string
        negate_condition = optional(bool, false)
        match_values     = list(number)
      })), [])
      host_name_conditions = optional(list(object({
        operator         = string
        match_values     = optional(list(string))
        transforms       = optional(list(string))
        negate_condition = optional(bool, false)
      })), [])
      ssl_protocol_conditions = optional(list(object({
        match_values     = list(string)
        operator         = optional(string, "Equal")
        negate_condition = optional(bool, false)
      })), [])
    }))
  }))
```

Default: `{}`

### <a name="input_front_door_secrets"></a> [front\_door\_secrets](#input\_front\_door\_secrets)

Description:   Manages a map of Front Door (standard/premium) Secrets.

  - `name` - (Required) The name which should be used for this Front Door Secret.
  - `key_vault_certificate_id` - (Required) The ID of the Key Vault certificate resource to use.  
  Example Input:

  ```terraform
  front_door_secrets = {
    secret1_key = {
      name                     = "Front-door-certificate"
      key_vault_certificate_id = azurerm_key_vault_certificate.keyvaultcert.versionless_id
    }
  }
```

Type:

```hcl
map(object({
    name                     = string
    key_vault_certificate_id = string
  }))
```

Default: `{}`

### <a name="input_front_door_security_policies"></a> [front\_door\_security\_policies](#input\_front\_door\_security\_policies)

Description:   Manages a map of Front Door (standard/premium) Security Policies.

  - `name` - (Required) The name which should be used for this Front Door Security Policy. Possible values must not be an empty string.
  - `firewall` - (Required) An firewall block as defined below: -
  - `front_door_firewall_policy_key` - (Required) the key of Front Door Firewall Policy that should be linked to this Front Door Security Policy.
  - `association` - (Required) An association block as defined below:-
  - `domain_keys` - (Optional) list of the domain keys to associate with the firewall policy. Provide either domain keys or endpoint keys or both.
  - `endpoint_keys` - (Optional) list of the endpoint keys to associate with the firewall policy. Provide either domain keys or endpoint keys or both.
  - `patterns_to_match` - (Required) The list of paths to match for this firewall policy. Possible value includes /*  
  Example Input:

  ```terraform
  front_door_security_policies = {
    secpol1_key = {
      name = "firewallpolicyforep1cd1"
      firewall = {
        front_door_firewall_policy_key = "fd_waf1_key"
        association = {
          endpoint_keys     = ["ep1_key"]
          domain_keys       = ["cd1_key"]
          patterns_to_match = ["/*"]
        }
      }
    }
  }
```

Type:

```hcl
map(object({
    name = string
    firewall = object({
      front_door_firewall_policy_key = string
      association = object({
        domain_keys       = optional(list(string), [])
        endpoint_keys     = optional(list(string), [])
        patterns_to_match = list(string)
      })
    })
  }))
```

Default: `{}`

### <a name="input_lock"></a> [lock](#input\_lock)

Description:   Controls the Resource Lock configuration for this resource. The following properties can be specified:

  - `kind` - (Required) The type of lock. Possible values are `\"CanNotDelete\"` and `\"ReadOnly\"`.
  - `name` - (Optional) The name of the lock. If not specified, a name will be generated based on the `kind` value. Changing this forces the creation of a new resource.  
  Example Input:

  ```terraform
  lock = {
      name = "lock-cdnprofile"
      kind = "CanNotDelete"
  }
```

Type:

```hcl
object({
    kind = string
    name = optional(string, null)
  })
```

Default: `null`

### <a name="input_managed_identities"></a> [managed\_identities](#input\_managed\_identities)

Description:   Controls the Managed Identities configuration on this resource. The following properties can be specified:

  - `system_assigned` - (Optional) Specifies if the System Assigned Managed Identity should be enabled.
  - `user_assigned_resource_ids` - (Optional) Specifies a list of User Assigned Managed Identity resource IDs to be assigned to this resource.  
  Example Input:

  ```terraform
  managed_identities = {
    system_assigned = true
    user_assigned_resource_ids = [
      azurerm_user_assigned_identity.identity_for_keyvault.id
    ]
  }
```

Type:

```hcl
object({
    system_assigned            = optional(bool, false)
    user_assigned_resource_ids = optional(set(string), [])
  })
```

Default: `{}`

### <a name="input_metric_alerts"></a> [metric\_alerts](#input\_metric\_alerts)

Description:   Manages a map of Metric Alerts to create on the cdn/Front door profile.

  - `name` - (Required) The name of the metric alert.Changing this forces a new resource to be created.
  - `auto_mitigate` - (Optional) If set to true, automatically mitigates the alert. Defaults to `true`.
  - `description` - (Optional) The description of the metric alert.
  - `enabled` - (Optional) If set to true, enables the metric alert. Defaults to `true`.
  - `frequency` - (Optional) The frequency of the metric alert. Possible values are `PT1M`, `PT5M`, `PT15M`, `PT30M` and `PT1H`. Defaults to `PT1M`.
  - `severity` - (Optional) The severity of the metric alert. Possible values are `0`, `1`, `2`, `3` and `4`. Defaults to `3`.
  - `target_resource_type` - (Optional) The type of the target resource. This is Required when using a Subscription as scope, a Resource Group as scope or Multiple Scopes.
  - `target_resource_location` - (Optional) The location of the target resource. This is Required when using a Subscription as scope, a Resource Group as scope or Multiple Scopes.
  - `window_size` - (Optional) The period of time that is used to monitor alert activity, represented in ISO 8601 duration format. This value must be greater than `frequency`. Possible values are `PT1M`, `PT5M`, `PT15M`, `PT30M`, `PT1H`, `PT6H`, `PT12H` and `P1D`. Defaults to `PT5M`.
  - `tags` - (Optional) A map of tags to assign to the metric alert.
  - `actions` - (Optional) A list of actions blocks as defined below:-
    - `action_group_id` - (Required) The ID of the action group, can be sourced from the `azurerm_monitor_action_group` resource.
    - `webhook_properties` - (Optional) A map of webhook properties.
  - `criterias` - (Optional) A list of criterias blocks as defined below:-
    - `metric_namespace` - (Required) The namespace of the metric.
    - `metric_name` - (Required) The name of the metric.
    - `aggregation` - (Required) The statistic that runs over the metric values. Possible values are `Average`, `Count`, `Minimum`, `Maximum` and `Total`.
    - `operator` - (Required) The operator of the metric. Possible values are `Equals`, `GreaterThan`, `GreaterThanOrEqual`, `LessThan` and `LessThanOrEqual`.
    - `threshold` - (Required) The criteria threshold value that activates the alert.
    - `skip_metric_validation` - (Optional) If set to true, skips the validation of the metric. Defaults to `false`.
    - `dimensions` - (Optional) A list of dimensions blocks as defined below:-
      - `name` - (Required) The name of the dimension.
      - `operator` - (Required) The operator of the dimension. Possible values are `Include`, `Exclude` and `StartsWith`.
      - `values` - (Required) The values of the dimension.
  - `dynamic_criterias` - (Optional) A list of dynamic\_criteria blocks as defined below:-
    - `alert_sensitivity` - (Required) The sensitivity of the alert. Possible values are `Low`, `Medium` and `High`.
    - `aggregation` - (Required) The aggregation type of the metric. Possible values are `Average`, `Count`, `Minimum`, `Maximum` and `Total`.
    - `operator` - (Required) The operator of the metric. Possible values are `GreaterThan`, `LessThan`, `GreaterOrLessThan`.
    - `dimension` - (Optional) A list of dimension blocks as defined below:-
      - `name` - (Required) The name of the dimension.
      - `operator` - (Required) The operator of the dimension. Possible values are `Include`, `Exclude` and `StartsWith`.
      - `values` - (Required) The values of the dimension.
    - `evaluation_failure_count` - (Optional) The number of consecutive breaches of the threshold required to trigger an alert. Defaults to `4`.
    - `evaluation_total_count` - (Optional) The number of consecutive evaluations required to trigger an alert.The lookback time window is calculated based on the aggregation granularity (window\_size) and the selected number of aggregated points. Defaults to `4`.
    - `ignore_data_before` - (Optional) The ISO8601 date from which to start learning the metric historical data and calculate the dynamic thresholds.
    - `metric_namespace` - (Required) The namespace of the metric.
    - `metric_name` - (Required) The name of the metric.
    - `skip_metric_validation` - (Optional) If set to true, skips the validation of the metric. Defaults to `false`.
  - `application_insights_web_test_location_availability_criterias` - (Optional) A list of application\_insights\_web\_test\_location\_availability\_criteria blocks as defined below:-
    - `component_id` - (Required) The ID of the Application Insights component.
    - `failed_location_count` - (Required) The number of failed locations.
    - `web_test_id` - (Required) The ID of the web test.

  Example Input:

  ```terraform

  metric_alerts = {
    alert1 = {
      name                = "1st criterion"
      description         = "Action will be triggered when ByteHitRatio is less than 90."
      enabled             = false
      frequency           = "PT5M"
      severity            = 2
      target_resource_type = "Microsoft.Cdn/profiles"
      window_size         = "PT30M"
      tags                = {
        environment = "AVM-Test"
      }
      criterias = [{
        metric_namespace = "Microsoft.Cdn/profiles"
        metric_name      = "ByteHitRatio"
        aggregation      = "Average"
        operator         = "LessThan"
        threshold        = 90
      }]
      actions = [{
        action_group_id = azurerm_monitor_action_group.example.id
      }]
    }

```

Type:

```hcl
map(object({
    name = string
    criterias = optional(list(object({
      metric_namespace       = string
      metric_name            = string
      aggregation            = string # Possible values are Average, Count, Minimum, Maximum and Total
      operator               = string # Possible values are Equals, GreaterThan, GreaterThanOrEqual, LessThan and LessThanOrEqual
      threshold              = number
      skip_metric_validation = optional(bool, false)
      dimensions = optional(list(object({
        name     = string
        operator = string
        values   = list(string)
      })))
    })), [])
    actions = optional(list(object({
      action_group_id    = string
      webhook_properties = optional(map(string))
    })), [])
    dynamic_criterias = optional(list(object({
      alert_sensitivity = string # Possible values are 'Low', 'Medium' and 'High'
      aggregation       = string # Possible values are 'Average', 'Count', 'Minimum', 'Maximum' and 'Total'.
      operator          = string # Possible values are 'GreaterThan', 'LessThan', 'GreaterOrLessThan'.
      dimension = optional(list(object({
        name     = string
        operator = string # Possible values are 'Include', 'Exclude' and 'StartsWith'.
        values   = list(string)
      })), [])
      evaluation_failure_count = optional(number, 4)
      evaluation_total_count   = optional(number, 4)
      ignore_data_before       = optional(string) # The ISO8601 date from which to start learning the metric historical data and calculate the dynamic thresholds.
      metric_namespace         = string
      metric_name              = string
      skip_metric_validation   = optional(bool, false)
    })), [])
    application_insights_web_test_location_availability_criterias = optional(list(object({
      component_id          = string
      failed_location_count = number
      web_test_id           = string
    })), [])
    auto_mitigate            = optional(bool, true)
    description              = optional(string)
    enabled                  = optional(bool, true)
    frequency                = optional(string, "PT1M") # Possible values are PT1M, PT5M, PT15M, PT30M and PT1H
    severity                 = optional(number, 3)      # Possible values are 0, 1, 2, 3 and 4
    target_resource_type     = optional(string)         # This is Required when using a Subscription as scope, a Resource Group as scope or Multiple Scopes.
    target_resource_location = optional(string)         # This is Required when using a Subscription as scope, a Resource Group as scope or Multiple Scopes.
    window_size              = optional(string, "PT5M") # This value must be greater than 'frequency'. Possible values are PT1M, PT5M, PT15M, PT30M, PT1H, PT6H, PT12H and P1D
    tags                     = optional(map(string))
  }))
```

Default: `{}`

### <a name="input_response_timeout_seconds"></a> [response\_timeout\_seconds](#input\_response\_timeout\_seconds)

Description: Specifies the maximum response timeout in seconds. Possible values are between 16 and 240 seconds (inclusive). Defaults to 120 seconds.

Type: `number`

Default: `120`

### <a name="input_role_assignments"></a> [role\_assignments](#input\_role\_assignments)

Description:   A map of role assignments to create on the cdn/Front door profile. The map key is deliberately arbitrary to avoid issues where map keys maybe unknown at plan time.

  - `role_definition_id_or_name` - The ID or name of the role definition to assign to the principal.
  - `principal_id` - The ID of the principal to assign the role to.
  - `description` - (Optional) The description of the role assignment.
  - `skip_service_principal_aad_check` - (Optional) If set to true, skips the Azure Active Directory check for the service principal in the tenant. Defaults to false.
  - `condition` - (Optional) The condition which will be used to scope the role assignment.
  - `condition_version` - (Optional) The version of the condition syntax. Leave as `null` if you are not using a condition, if you are then valid values are '2.0'.
  - `delegated_managed_identity_resource_id` - (Optional) The delegated Azure Resource Id which contains a Managed Identity. Changing this forces a new resource to be created. This field is only used in cross-tenant scenario.
  - `principal_type` - (Optional) The type of the `principal_id`. Possible values are `User`, `Group` and `ServicePrincipal`. It is necessary to explicitly set this attribute when creating role assignments if the principal creating the assignment is constrained by ABAC rules that filters on the PrincipalType attribute.

  > Note: only set `skip_service_principal_aad_check` to true if you are assigning a role to a service principal.  
  Example Input:

  ```terraform
  role_assignments = {
    role_assignment_2 = {
      role_definition_id_or_name       = "Reader"
      principal_id                     = data.azurerm_client_config.current.object_id #"125****-c***-4f**-**0d-******53b5**"
      description                      = "Example role assignment 2 of reader role"
      skip_service_principal_aad_check = false
      principal_type                   = "ServicePrincipal"
      condition                        = "@Resource[Microsoft.Storage/storageAccounts/blobServices/containers:ContainerName] StringEqualsIgnoreCase 'foo_storage_container'"
      condition_version                = "2.0"
    }
  }
```

Type:

```hcl
map(object({
    role_definition_id_or_name             = string
    principal_id                           = string
    description                            = optional(string, null)
    skip_service_principal_aad_check       = optional(bool, false) # Note: only set `skip_service_principal_aad_check` to true if you are assigning a role to a service principal.
    condition                              = optional(string, null)
    condition_version                      = optional(string, null)
    delegated_managed_identity_resource_id = optional(string, null)
    principal_type                         = optional(string, null)
  }))
```

Default: `{}`

### <a name="input_sku"></a> [sku](#input\_sku)

Description: The SKU name of the Azure Front Door. Default is `Standard`. Possible values are `standard` and `premium`.SKU name for CDN can be 'Standard\_ChinaCdn' or 'Standard\_Microsoft'

Type: `string`

Default: `"Standard_AzureFrontDoor"`

### <a name="input_tags"></a> [tags](#input\_tags)

Description: Map of tags to assign to the CDN profile resource.

Type: `map(string)`

Default: `null`

## Outputs

The following outputs are exported:

### <a name="output_cdn_endpoint_custom_domains"></a> [cdn\_endpoint\_custom\_domains](#output\_cdn\_endpoint\_custom\_domains)

Description: CDN endpoint custom domains output object

### <a name="output_cdn_endpoints"></a> [cdn\_endpoints](#output\_cdn\_endpoints)

Description: CDN endpoint output object

### <a name="output_frontdoor_custom_domains"></a> [frontdoor\_custom\_domains](#output\_frontdoor\_custom\_domains)

Description: Azure front door custom domains output object

### <a name="output_frontdoor_endpoints"></a> [frontdoor\_endpoints](#output\_frontdoor\_endpoints)

Description: Azure front door endpoint output object

### <a name="output_frontdoor_firewall_policies"></a> [frontdoor\_firewall\_policies](#output\_frontdoor\_firewall\_policies)

Description: Azure front door firewall policies output object

### <a name="output_frontdoor_origin_groups"></a> [frontdoor\_origin\_groups](#output\_frontdoor\_origin\_groups)

Description: Azure front door origin groups output object

### <a name="output_frontdoor_origins"></a> [frontdoor\_origins](#output\_frontdoor\_origins)

Description: Azure front door origins output object

### <a name="output_frontdoor_rule_sets"></a> [frontdoor\_rule\_sets](#output\_frontdoor\_rule\_sets)

Description: Azure front door rule sets output object

### <a name="output_frontdoor_rules"></a> [frontdoor\_rules](#output\_frontdoor\_rules)

Description: Azure front door rules output object

### <a name="output_frontdoor_security_policies"></a> [frontdoor\_security\_policies](#output\_frontdoor\_security\_policies)

Description: Azure front door security policies output object

### <a name="output_resource"></a> [resource](#output\_resource)

Description: Full resource output object

### <a name="output_resource_id"></a> [resource\_id](#output\_resource\_id)

Description: The resource id of the Front door profile

### <a name="output_resource_name"></a> [resource\_name](#output\_resource\_name)

Description: The resource name of the Front door profile

### <a name="output_system_assigned_mi_principal_id"></a> [system\_assigned\_mi\_principal\_id](#output\_system\_assigned\_mi\_principal\_id)

Description: The system assigned managed identity of the front door profile

## Modules

No modules.

<!-- markdownlint-disable-next-line MD041 -->
## Data Collection

The software may collect information about you and your use of the software and send it to Microsoft. Microsoft may use this information to provide services and improve our products and services. You may turn off the telemetry as described in the repository. There are also some features in the software that may enable you and Microsoft to collect data from users of your applications. If you use these features, you must comply with applicable law, including providing appropriate notices to users of your applications together with a copy of Microsoft’s privacy statement. Our privacy statement is located at <https://go.microsoft.com/fwlink/?LinkID=824704>. You can learn more about data collection and use in the help documentation and our privacy statement. Your use of the software operates as your consent to these practices.
<!-- END_TF_DOCS -->