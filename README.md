# cartov2-gitops

To install this package on a run cluster:

```
---
apiVersion: kappctrl.k14s.io/v1alpha1
kind: App
metadata:
 name: mypackage
 namespace: run-ns
spec:
 cluster:
   namespace: run-ns
 fetch:
 - git:
     url: https://github.com/garethjevans-test/cartov2-gitops
     ref: origin/main
     subPath: mypackage.example.com/packages
 - git:
     url: https://github.com/garethjevans-test/cartov2-gitops
     ref: origin/main
     subPath: mypackage.example.com/staging
 template:
 - ytt: {}

  deploy:
 - kapp:
     intoNs: run-ns
     rawOptions: ["--dangerous-allow-empty-list-of-resources=true"]
```
