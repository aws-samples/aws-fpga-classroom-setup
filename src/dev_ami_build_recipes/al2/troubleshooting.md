## Troubleshooting AMI Builds

**Incorrect Region**

Only the `us-east- 1` region is supported. If you used a different region, then you may see the following error:

```
Build 'amazon-ebs' errored after 841 milliseconds 858
microseconds: error validating regions: UnauthorizedOperation:
You are not authorized to perform this operation. status
code: 403, request id: c9d0a940-ba62-4f04-9b8f-8a67f2580b
```

**Build completes, but times out with `AMI: Failed with ResourceNotReady` error**

Due to the size of the AMI, packer can time out before the AMI is fully available. This is expected and the AMI will still be built. Wait a couple of hours and check your AWS account. You should see the AMI.
```
Build 'amazon-ebs' errored after 1 hour 13 minutes: Error waiting
for AMI: Failed with ResourceNotReady error, which can have a
variety of causes. For help troubleshooting, check our docs:
https://www.packer.io/docs/builders/amazon.html#resourcenotready-
error

original error: ResourceNotReady: exceeded wait attempts

==> Wait completed after 1 hour 13 minutes

==> Some builds didn't complete successfully and had errors:
--> amazon-ebs: Error waiting for AMI: Failed with
ResourceNotReady error, which can have a variety of causes. For
help troubleshooting, check our docs:
https://www.packer.io/docs/builders/amazon.html#resourcenotready-

error original error: ResourceNotReady: exceeded wait attempts

==> Builds finished but no artifacts were created.
```
**Credential Issues**

If your credentials are incorrect or missing, you will see the following error. Check your credentials and rerun the AMI build process.

```
Build 'amazon-ebs' errored after 525 milliseconds 875
microseconds: No valid credential sources found for AWS Builder.
Please see https://www.packer.io/docs/builders/amazon#specifying-
amazon- credentials for more information on providing
credentials for the AWS Builder.
```

**Incorrect Indentation in Ansible yaml File**

Incorrect indentation in the xilinx_playbook.yaml file will result in an error similar to this:

```
Build 'amazon-ebs' errored after 841 milliseconds 858
microseconds: error validating regions: Unauthorized Operation:

You are not authorized to perform this operation. status
code: 403, request id: c9d0a940-ba62-4f04-9b8f-8a67f2580b
```

To fix, ensure you are using two spaces as your indent instead of tabs.
