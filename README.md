# Heytaco Anywhre Helm Charts

This repository hosts official Helm charts for Heytaco Anywhere. These charts are used to deploy Heytaco Anywhere to Kubernetes.

## Install Helm

Read and follow the Helm installation guide.

## Add the Heytaco Anywhere Helm Chart repo

In order to be able to use the charts in this repository, add the name and URL to your Helm client:

```console
$ helm repo add heytaco-anywhere https://heytaco-anywhere.chat/helm-chart/
$ helm repo update
```

## Installing Heytaco Anywhere

See the [Heytaco Anywhere Server Installation](./docs/install.md).

## Configuring Heytaco Anywhere

See [values.yaml](./charts/heytaco-anywhere/values.yaml) to see the Chart's default values. 

To adjust an existing Heytaco Anywhere install's configuration:

```console
# If you have a values file:
$ helm upgrade heytaco-anywhere heytaco-anywhere/heytaco-anywhere --namespace heytaco-anywhere --values values.overrides.yaml
# If you want to change one value and don't have a values file:
$ helm upgrade heytaco-anywhere heytaco-anywhere/heytaco-anywhere --namespace heytaco-anywhere --reuse-values --set someKey=someVal
```

## Upgrading Heytaco Anywhere

Read the release notes to make sure there are no backwards incompatible changes.  Make adjustments to your values as needed, then run `helm upgrade`.


```console
# This pulls the latest version of the heytaco-anywhere chart from the repo.
$ helm repo update
$ helm upgrade heytaco-anywhere heytaco-anywhere/heytaco-anywhere --namespace heytaco-anywhere --values values.overrides.yaml
```

## Uninstalling Heytaco Anywhere

To uninstall/delete the `heytaco-anywhere` deployment in the `heytaco-anywhere` namespace:

```console
$ helm delete heytaco-anywhere --namespace heytaco-anywhere
```

## Documentation

See the Heytaco Anywhere documentation site for more information.

## License

BSD 3-Clause License
