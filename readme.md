Introduction
---
This is a collection of [upstream-community-operators](https://github.com/operator-framework/community-operators/tree/master/upstream-community-operators) from [OperatorHub.io](https://operatorhub.io/) that can be deployed on OpenShift.

To add to OpenShift, create a `CatalogSource` in the `openshift-marketplace` namespace. 

For example:
```
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  name: grafana-operator
  namespace: openshift-marketplace
spec:
  displayName: Grafana Operator
  sourceType: grpc
  image: quay.io/ltsai/grafana-operator-registry:3.2.0
```

Build instructions
---

If you wish to build a operator registry for grafana, you will need the [Operator Package Manager](https://github.com/operator-framework/operator-registry/releases) tool. 

```
$ tree grafana-operator/
grafana-operator/
├── 1.3.0
│   ├── grafana-operator.v1.3.0.clusterserviceversion.yaml
│   ├── grafanadashboards.integreatly.org.crd.yaml
│   ├── grafanadatasources.integreatly.org.crd.yaml
│   └── grafanas.integreatly.org.crd.yaml
├── 2.0.0
│   ├── grafana-operator.v2.0.0.clusterserviceversion.yaml
│   ├── grafanadashboards.integreatly.org.crd.yaml
│   ├── grafanadatasources.integreatly.org.crd.yaml
│   └── grafanas.integreatly.org.crd.yaml
├── 3.0.2
│   ├── grafana-operator.v3.0.2.clusterserviceversion.yaml
│   ├── grafanadashboards.integreatly.org.crd.yaml
│   ├── grafanadatasources.integreatly.org.crd.yaml
│   └── grafanas.integreatly.org.crd.yaml
├── 3.2.0
│   ├── grafana-operator.v3.2.0.clusterserviceversion.yaml
│   ├── grafanadashboards.integreatly.org.crd.yaml
│   ├── grafanadatasources.integreatly.org.crd.yaml
│   └── grafanas.integreatly.org.crd.yaml
└── grafana-operator.package.yaml
```

1. Build an operator bundle image

```
# opm alpha bundle build --directory grafana-operator/3.0.2 --package grafana-operator  -t registry.lab.ltsai.com/grafana-operator-manifest-bundle:3.0.2 --image-builder docker --channels stable,beta --default stable
# docker push registry.lab.ltsai.com/grafana-operator-manifest-bundle:3.0.2
``` 

2. Build the index

```
# opm index add --bundles registry.lab.ltsai.com/grafana-operator-manifest-bundle:3.0.2 --tag registry.lab.ltsai.com/grafana-operator-registry:3.0.2 --container-tool docker --permissive 
# docker push registry.lab.ltsai.com/grafana-operator-registry:3.0.2
```

Links
===
* https://github.com/operator-framework/operator-registry
* https://github.com/operator-framework/operator-registry/blob/master/docs/design/operator-bundle.md
* https://github.com/operator-framework/operator-registry/blob/master/docs/design/opm-tooling.md
