---
subcategory: "EC2"
layout: "aws"
page_title: "AWS: aws_launch_template"
description: |-
  Provides a Launch Template data source.
---

# Data Source: aws_launch_template

Provides information about a Launch Template.

## Example Usage

```terraform
data "aws_launch_template" "default" {
  name = "my-launch-template"
}
```

### Filter

```terraform
data "aws_launch_template" "test" {
  filter {
    name   = "launch-template-name"
    values = ["some-template"]
  }
}
```

## Argument Reference

The following arguments are supported:

* `filter` - (Optional) Configuration block(s) for filtering. Detailed below.
* `id` - (Optional) The ID of the specific launch template to retrieve.
* `name` - (Optional) The name of the launch template.
* `tags` - (Optional) A map of tags, each pair of which must exactly match a pair on the desired Launch Template.

### filter Configuration Block

The following arguments are supported by the `filter` configuration block:

* `name` - (Required) The name of the filter field. Valid values can be found in the [EC2 DescribeLaunchTemplates API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeLaunchTemplates.html).
* `values` - (Required) Set of values that are accepted for the given filter field. Results will be selected if any given value matches.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `arn` - Amazon Resource Name (ARN) of the launch template.
* `id` - The ID of the launch template.
* `default_version` - The default version of the launch template.
* `latest_version` - The latest version of the launch template.
* `description` - Description of the launch template.
* `block_device_mappings` - Specify volumes to attach to the instance besides the volumes specified by the AMI.
* `credit_specification` - Customize the credit specification of the instance. See [Credit
  Specification](#credit-specification) below for more details.
* `disable_api_termination` - If `true`, enables [EC2 Instance
  Termination Protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html#Using_ChangingDisableAPITermination)
* `ebs_optimized` - If `true`, the launched EC2 instance will be EBS-optimized.
* `elastic_gpu_specifications` - The elastic GPU to attach to the instance. See [Elastic GPU](#elastic-gpu)
  below for more details.
* `iam_instance_profile` - The IAM Instance Profile to launch the instance with. See [Instance Profile](#instance-profile)
  below for more details.
* `image_id` - The AMI from which to launch the instance.
* `instance_initiated_shutdown_behavior` - Shutdown behavior for the instance. Can be `stop` or `terminate`.
  (Default: `stop`).
* `instance_market_options` - The market (purchasing) option for the instance.
  below for details.
* `instance_type` - The type of the instance.
* `kernel_id` - The kernel ID.
* `key_name` - The key name to use for the instance.
* `metadata_options` - The metadata options for the instance.
    * `http_endpoint` - The state of the metadata service: `enabled`, `disabled`.
    * `http_tokens` - If session tokens are required: `optional`, `required`.
    * `http_put_response_hop_limit` - The desired HTTP PUT response hop limit for instance metadata requests.
    * `http_protocol_ipv6` - The state of IPv6 endpoint for the instance metadata service: `enabled`, `disabled`.
* `monitoring` - The monitoring option for the instance.
* `network_interfaces` - Customize network interfaces to be attached at instance boot time. See [Network
  Interfaces](#network-interfaces) below for more details.
* `placement` - The placement of the instance.
* `ram_disk_id` - The ID of the RAM disk.
* `security_group_names` - A list of security group names to associate with. If you are creating Instances in a VPC, use
  `vpc_security_group_ids` instead.
* `vpc_security_group_ids` - A list of security group IDs to associate with.
* `tag_specifications` - The tags to apply to the resources during launch.
* `tags` - (Optional) A map of tags to assign to the launch template.
* `user_data` - The Base64-encoded user data to provide when launching the instance.
* `hibernation_options` - The hibernation options for the instance.
* `enclave_options` - The enclave options of the Instance.
    * `enabled` - Whether Nitro Enclaves are enabled.

