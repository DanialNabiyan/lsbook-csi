
# lsdisk CSI

Lsdisk is a CSI driver for kubernetes that can use in on-permise and baremetal environment

## How lsdisk Work?
lsdisk create volume in disk  that you set storage model in storageclass parameters

Example:
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: hdd-fast
provisioner: lsdisk.driver
reclaimPolicy: Delete
volumeBindingMode: WaitForFirstConsumer
allowVolumeExpansion: true
parameters:
  storagemodel: EG002400JXLWC
```

lsdisk find node that have disk with specified 
**storagemodel** in storage class and create volume in that disk

lsdisk have **Two** main component

* lsdisk-controller (statefulset)
* lsdisk-node (daemonset)

### Acknowledgements
 - [CSI developer](https://kubernetes-csi.github.io/docs/)
 - [CSI Specification ](https://github.com/container-storage-interface/spec/tree/master)