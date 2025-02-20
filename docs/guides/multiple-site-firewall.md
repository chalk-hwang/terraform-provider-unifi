---
subcategory: ""
page_title: "Manage Firewall Rules for Multiple Sites - Unifi Provider"
description: |-
  An example of applying firewall rules to multiple sites.
---

# Manage Firewall Rules for Multiple Sites

The provider takes a default site value but all resources in the provider should allow overriding of the
site you are managing. In order to apply and manage a firewall rule across multiple sites, you simply
need to provide different values for the `site` attribute to `unifi_firewall_rule`:

```terraform
resource "unifi_firewall_rule" "rule" {
  # list of sites
  for_each = toset(["default", "vq98kwez", "bfa2l6i7"])
  # use the key of the list as the site value
  site = each.key

  name    = "drop all"
  action  = "drop"
  ruleset = "LAN_IN"

  rule_index = 2011

  protocol = "all"

  dst_address = var.ip_address
}
```

You could optionally load lists of sites from JSON/CSV, variables, or other sources.

When you apply this configuration it will create the same firewall rule on every site in the list.
If you need to update the rule, you simply make an update to the rule definition and Terraform will
apply/update it across all the sites. If you add / or remove a site from the list, Terraform will also
handle creating or removing the rule on the subsequent `terraform apply`.
