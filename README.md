# Assume AWS Role for GitHub Actions
This action allows to assume AWS role in other account.
The official action is not sufficient for assuming AWS role account in different accounts without access and secret keys.

> The primary reason this action exists is to use it in self-hosted GitHub runners in Kubernetes with already attached IAM role through service account and assume AWS role in other account.

# Usage
```yaml
jobs:  
  test_new_action:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Repo
      uses: actions/checkout@v3

    - uses: st-vasyl/assume-aws-role-action@v1
      with:
        role-arn: arn:aws:iam::<ACCOUNT_ID>:role/<ROLE_NAME>

    - run: aws s3 ls
```