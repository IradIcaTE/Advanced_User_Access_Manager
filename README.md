# Advanced User Access Manager

This Jenkins pipeline checks if a given username is allowed to proceed with the environment provisioning.

## How it works:
- Input a username at the start of the pipeline.
- If the username exists in the blocked list (defined in the `BLOCKED_USERS` environment variable), access is denied.
- Otherwise, the user is provisioned.

## To Run:
1. Open Jenkins and run the pipeline.
2. Provide the `USERNAME` when prompted.
