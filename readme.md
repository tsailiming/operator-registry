This is a collection of upstream-community operators from OperatorHub.IO that can be deployed on OpenShift.

```
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  name: grafana-operator
  namespace: openshift-marketplace
spec:
  displayName: Grafana Operator
  sourceType: grpc
  image: quay.lab.ltsai.com/quay.io/ltsai/grafana-operator-registry:3.2.0
```
