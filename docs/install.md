# Heytaco Anywhere Server Installation

## Disclaimer

This page is not intended to be a comprehensive guide to installing Heytaco Anywhere. It will only cover the Kubernetes-specific parts of the process.

## Configuration 

In order to install the chart, you'll need to pass in additional configuration. This configuration comes in the form of Helm values, which are key/value pairs.

```yaml
env: 
  # REQUIRED: Set the user-visible hostname.
  #
  HEYTACO_ANYWHERE_SERVER_HOST: ""
  # REQUIRED: The protocol to pair with the value in HEYTACO_ANYWHERE_SERVER_HOST (http or https).
  #
  HEYTACO_ANYWHERE_SERVER_PROTO: https
  # REQUIRED: The secret of Heytaco! app.
  # You can get the secret from https://heytaco.chat/team/apps.
  #
  HEYTACO_ANYWHERE_HEYTACO_APP_SECRET: ""

  # Slack-specific variables.
  #
  HEYTACO_ANYWHERE_SLACK_CHANNEL:
  HEYTACO_ANYWHERE_SLACK_CLIENT_ID:
  HEYTACO_ANYWHERE_SLACK_CLIENT_SECRET:
```

Copy these into a new file, which we'll call `values.overrides.yaml`. Adjust the included defaults to reflect your environment.

## Run the installation

Create the namespace to install Heytaco Anywhere in if it does not already exist:

```console
$ kubectl create ns heytaco-anywhere
namespace/heytaco-anywhere created
```

Run `helm` install with your values provided:

```console
$ helm install --namespace heytaco-anywhere heytaco-anywhere heytaco-anywhere/heytaco-anywhere  -f values.overrides.yaml
```

Once the install command is ran, your Kubernetes cluster will begin creating resources. To see how your deploy is shaping up, run:

```console
$ kubectl --namespace heytaco-anywhere get pods
NAME                                 READY   STATUS    RESTARTS   AGE
heytaco-anywhere-76d6bb8968-3d5n9               1/1     Running   0          2m
```
