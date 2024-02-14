# README

Requires VSCode Dev Containers extension and Docker Desktop.

## Why

Provide a containerized python environment for developing python/sagemaker
and make use of tooling such as `granted`.

- source code files are available in container and editable via VSC
- git configuration is available within the devcontainer

## How

How to log in to AWS.

```shell
# to launch granted/assume
aws-env

# run aws cli commands
aws s3 ls

aws sagemaker list-user-profiles --region us-east-1
aws sagemaker list-training-jobs --region us-east-1
aws sagemaker list-domains --region us-east-1

# unset AWS Profile
aws-unset

```

## References

- <https://stackoverflow.com/questions/68869092/aws-sso-login-to-credentials-as-environment-variables>
- <https://github.com/ohmyzsh/docker/blob/main/ohmyzsh/Dockerfile>
- <https://github.com/deluan/zsh-in-docker/blob/master/zsh-in-docker.sh>
- <https://medium.com/@josh.armitage/using-granted-in-a-dev-container-e355a3045c70>
