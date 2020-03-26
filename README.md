This AWS Lambda function is invoked after a HashiCorp Vault cluster is brought
up in an AWS autoscaling group. The function chooses a random, healthy node and
initializes it (the other Vault nodes are configured to automatically form the
cluster once this happens.)

The resulting initial root token and recovery keys (assuming the Vault cluster
is using auto-unseal) are stored in AWS Secrets Manager.

This Lambda function uses the **AutoScalingGroupName** that is received from the
[event](https://docs.aws.amazon.com/autoscaling/ec2/userguide/cloud-watch-events.html#terminate-lifecycle-action).