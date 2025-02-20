---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "unifi_radius_profile Resource - terraform-provider-unifi"
subcategory: ""
description: |-
  unifi_radius_profile manages RADIUS profiles.
---

# unifi_radius_profile (Resource)

`unifi_radius_profile` manages RADIUS profiles.

<!-- schema generated by tfplugindocs -->

## Schema

### Required

- `name` (String) The name of the profile.

### Optional

- `accounting_enabled` (Boolean) Specifies whether to use RADIUS accounting. Defaults to `false`.
- `acct_server` (Block List) RADIUS accounting servers. (see [below for nested schema](#nestedblock--acct_server))
- `auth_server` (Block List) RADIUS authentication servers. (see [below for nested schema](#nestedblock--auth_server))
- `interim_update_enabled` (Boolean) Specifies whether to use interim_update. Defaults to `false`.
- `interim_update_interval` (Number) Specifies interim_update interval. Defaults to `3600`.
- `site` (String) The name of the site to associate the settings with.
- `use_usg_acct_server` (Boolean) Specifies whether to use usg as a RADIUS accounting server. Defaults to `false`.
- `use_usg_auth_server` (Boolean) Specifies whether to use usg as a RADIUS authentication server. Defaults to `false`.
- `vlan_enabled` (Boolean) Specifies whether to use vlan on wired connections. Defaults to `false`.
- `vlan_wlan_mode` (String) Specifies whether to use vlan on wireless connections. Must be one of `disabled`, `optional`, or `required`. Defaults to ``.

### Read-Only

- `id` (String) The ID of the settings.

<a id="nestedblock--acct_server"></a>

### Nested Schema for `acct_server`

Required:

- `ip` (String) IP address of accounting service server.
- `xsecret` (String, Sensitive) RADIUS secret.

Optional:

- `port` (Number) Port of accounting service. Defaults to `1813`.

<a id="nestedblock--auth_server"></a>

### Nested Schema for `auth_server`

Required:

- `ip` (String) IP address of authentication service server.
- `xsecret` (String, Sensitive) RADIUS secret.

Optional:

- `port` (Number) Port of authentication service. Defaults to `1812`.
