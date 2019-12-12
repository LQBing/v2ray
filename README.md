# V2ray

[V2ray](https://github.com/LQBing/V2ray) aims to collect information about Kubernetes clusters. This information will help the Kubernetes development team to understand what people are doing with it, and to make it a better product.

## TL;DR;

```console
$ helm install stable/V2ray
```

## Introduction

This chart bootstraps a [V2ray](https://github.com/LQBing/V2ray) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites
  - Kubernetes 1.3+ with Beta APIs enabled

## Installing the Chart

Add this helm repo:

```console
$ helm repo add v2ray https://lqbing.github.io/v2ray
$ helm repo update
```

To install the chart with the release name `my-v2ray`:

```console
$ helm install v2ray/v2ray --name my-v2ray
```

The command deploys V2ray on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-v2ray` deployment:

```console
$ helm delete my-v2ray
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the V2ray chart and their default values.

Parameter | Description | Default
--- | --- | ---
`ss.method` | ss method | `aes-128-gcm`
`ss.port` | ss port | `1080`
`ss.password` | ss password |  Dynamically generated using `derivePassword` template function
`vmess.uuid` | Unique cluster ID | Dynamically generated using `uuidv4` template function
`vmess.port` | ss port | `9527`

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install stable/V2ray --name my-v2ray \
    --namespace v2ray \
    --set ss.port=1285 \
    --set ss.method=aes-128-gcm \
    --set ss.password=yq1htYOUZUmCdV8K \
    --set vmess.port=9958 \
    --set vmess.uuid=19339C6E-FD73-4787-BFD8-F710C8D8364E
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install stable/V2ray --name my-v2ray -f values.yaml
```

> **Tip**: You can use the default [values.yaml](values.yaml)
