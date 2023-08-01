

## Horizontal Pod Autoscaling (HPA)

The HPA automatically updates a workload resource to scale to the demand. This means if there is an increase in demand, more pods will be created. To see the script go to `mongodb-asg.yml` or `app-hpa.yml`.

### Commands:

```bash
kubectl create -f mongodb-asg.yml
kubectl get hpa
```
## Volumes in Kubernetes

Volumes in Kubernetes provide a way to store and persist data beyond the lifetime of a Pod. It enables data sharing and preservation across Pod restarts and rescheduling.

## Persistent Volume (PV)

A Persistent Volume (PV) is a storage resource in the cluster that exists independently of Pods. PVs are provisioned by the cluster administrator and can be dynamically provisioned or statically defined.

To create a PV, use the YAML file `app-pv.yml`:
`kubectl create -f app-pv.yml`

## Persistent Volume Claim (PVC)

A Persistent Volume Claim (PVC) is a request for storage by a user. It acts as a request for a specific amount of storage from the cluster's available PVs. Once a PVC is created, Kubernetes binds it to an appropriate PV.

To create a PVC, use the YAML file `app-pvc.yml`:
`kubectl create -f app-pvc.yml`
After creating the PVC, it will be bound to a suitable PV, and the Pod can use the volume for storing data.

## Check Persistent Volumes

To view the list of Persistent Volumes in your cluster, use the following command:

`kubectl get pv`