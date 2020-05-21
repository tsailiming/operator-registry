This is a collection of [upstream-community-operators](https://github.com/operator-framework/community-operators/tree/master/upstream-community-operators) from [OperatorHub.io](https://operatorhub.io/) that can be deployed on OpenShift.

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
