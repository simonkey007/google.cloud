# Contributing to the google.cloud collection

## Workflow summary

1. [Clone the repository](#cloning).
1. Make the desired code change.
1. [Run integration tests locally and ensure they pass](running-integration-tests).
1. Create a PR.

## Cloning

The `ansible-test` command expects that the repository is in a directory that matches it's collection,
under a directory `ansible_collections`. Clone ensuring that hierarchy:

```shell
mkdir -p $TARGET_DIR/ansible_collections/google
git clone <url> $TARGET_DIR/collections/google/cloud
```

## Running tests

### prequisites for all tests

- Install the `ansible` package.

## Running integration tests

### Integration testing prequisites

#### Installing personal GCP credentials

The integration tests for this module require the use of real GCP credentials, and must provide
ansible-test those values. They can be added by authoring the following in `tests/integration/cloud-config-gcp.ini`:

```
[default]
gcp_project: @PROJECT_ID
gcp_cred_file: @CRED_FILE
gcp_cred_kind: @CRED_KIND
gcp_cred_email: @EMAIL
```

#### Setting up the project for testing

Some of the setup of the project itself is done outside of the test,
and is expected to be configured beforehand.

For convenience, a bootstrap script is provided.

NOTE: running this script will make irreversible changes in your
GCP project (e.g. create an AppEngine project):

```bash
bash ./scripts/bootstrap-project.sh $PROJECT_ID $SERVICE_ACCOUNT_NAME
```

### Running

Run `ansible-test integration`. Currently some tests are disabled as [test are being verified and added](https://github.com/ansible-collections/google.cloud/issues/499).