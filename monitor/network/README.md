# OpenShift Network Monitor Tool

A tool to monitor the network usage for Nodes in OpenShift.

## Usage
To deploy this DaemonSet to a cluster:
```
oc new-project monitor-network-debug && oc project monitor-network-debug
oc adm policy add-scc-to-user privileged -z default
oc apply -f ./daemonset.yaml
```

To gather the metrics from the DaemonSet:
```
for POD in $(oc get pods -o name -n monitor-network-debug | grep monitor-network-daemonset); do
  echo "Gathering logs from Pod: ${POD:4}"
  oc cp ${POD:4}:/network-metrics.tar.gz "$(pwd)/${POD:4}-network-metrics.tar.gz"
done
```
