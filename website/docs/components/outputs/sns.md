---
title: sns
type: output
status: deprecated
categories: ["Services","AWS"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/output/sns.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

:::warning DEPRECATED
This component is deprecated and will be removed in the next major version release. Please consider moving onto [alternative components](#alternatives).
:::

Sends messages to an AWS SNS topic.


<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

<TabItem value="common">

```yaml
# Common config fields, showing default values
output:
  label: ""
  sns:
    topic_arn: ""
    message_group_id: ""
    message_deduplication_id: ""
    max_in_flight: 1
    metadata:
      exclude_prefixes: []
    region: eu-west-1
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
output:
  label: ""
  sns:
    topic_arn: ""
    message_group_id: ""
    message_deduplication_id: ""
    max_in_flight: 1
    metadata:
      exclude_prefixes: []
    timeout: 5s
    region: eu-west-1
    endpoint: ""
    credentials:
      profile: ""
      id: ""
      secret: ""
      token: ""
      role: ""
      role_external_id: ""
```

</TabItem>
</Tabs>

## Alternatives

This output has been renamed to [`aws_sns`](/docs/components/outputs/aws_sns).

### Credentials

By default Benthos will use a shared credentials file when connecting to AWS
services. It's also possible to set them explicitly at the component level,
allowing you to transfer data across accounts. You can find out more
[in this document](/docs/guides/cloud/aws).

## Performance

This output benefits from sending multiple messages in flight in parallel for
improved performance. You can tune the max number of in flight messages with the
field `max_in_flight`.

## Fields

### `topic_arn`

The topic to publish to.


Type: `string`  
Default: `""`  

### `message_group_id`

An optional group ID to set for messages.
This field supports [interpolation functions](/docs/configuration/interpolation#bloblang-queries).


Type: `string`  
Default: `""`  
Requires version 3.60.0 or newer  

### `message_deduplication_id`

An optional deduplication ID to set for messages.
This field supports [interpolation functions](/docs/configuration/interpolation#bloblang-queries).


Type: `string`  
Default: `""`  
Requires version 3.60.0 or newer  

### `max_in_flight`

The maximum number of messages to have in flight at a given time. Increase this to improve throughput.


Type: `int`  
Default: `1`  

### `metadata`

Specify criteria for which metadata values are sent as headers.


Type: `object`  
Requires version 3.60.0 or newer  

### `metadata.exclude_prefixes`

Provide a list of explicit metadata key prefixes to be excluded when adding metadata to sent messages.


Type: `array`  
Default: `[]`  

### `timeout`

The maximum period to wait on an upload before abandoning it and reattempting.


Type: `string`  
Default: `"5s"`  

### `region`

The AWS region to target.


Type: `string`  
Default: `"eu-west-1"`  

### `endpoint`

Allows you to specify a custom endpoint for the AWS API.


Type: `string`  
Default: `""`  

### `credentials`

Optional manual configuration of AWS credentials to use. More information can be found [in this document](/docs/guides/cloud/aws).


Type: `object`  

### `credentials.profile`

A profile from `~/.aws/credentials` to use.


Type: `string`  
Default: `""`  

### `credentials.id`

The ID of credentials to use.


Type: `string`  
Default: `""`  

### `credentials.secret`

The secret for the credentials being used.


Type: `string`  
Default: `""`  

### `credentials.token`

The token for the credentials being used, required when using short term credentials.


Type: `string`  
Default: `""`  

### `credentials.role`

A role ARN to assume.


Type: `string`  
Default: `""`  

### `credentials.role_external_id`

An external ID to provide when assuming a role.


Type: `string`  
Default: `""`  


