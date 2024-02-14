# README

Requires VSCode Dev Containers extension and Docker Desktop.

How to log in to AWS.

```shell
# to launch granted/assume
aws-env

aws s3 ls

aws sagemaker list-user-profiles --region us-east-1
aws sagemaker list-training-jobs --region us-east-1
aws sagemaker list-domains --region us-east-1

# to unset AWS Profile
aws-unset

```

## References

- <https://stackoverflow.com/questions/68869092/aws-sso-login-to-credentials-as-environment-variables>
- <https://github.com/ohmyzsh/docker/blob/main/ohmyzsh/Dockerfile>
- <https://github.com/deluan/zsh-in-docker/blob/master/zsh-in-docker.sh>

