## Summary

The `knife bootstrap` command established an SSH connection to the node, installed `chef-client`, downloaded the Learn Chef Apache cookbook on the node, and ran it. In one command, Chef carried out most of the steps you previously dealt with manually.

A powerful part of the `knife bootstrap` process is that you did not need to connect to or interact with the server directly. This enables you to further automate the process of provisioning and configuring your infrastructure. But if you'd like, you can connect to the server now to verify that everything is set up as you'd expect.