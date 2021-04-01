# OpenShift `tcpdump` Tool

A tool to capture network packets from multiple pods

## Installation

No particular installation is need for the bash script run, however, the tool
is written to be an `oc plugin`, so creating a soft link to
`oc-tools-tcpdump` will allow the tool to be invoked as `oc tools tcpdump`


```
## assuming ~/bin/ is in your PATH
ln -sf $PWD/oc-tools-tcpdump ~/bin/

## Verify by running
oc tools tcpdump -h
```

## Usage

```
# capture network traffic including the node traffic from all openshift dns pods
oc tools tcpdump -n openshift-dns


# capture network traffic from nginx (label app=nginx) pods only
# deployed to 'web' namespace

oc tools tcpdump --no-nodes -n web -l app=nginx
```



## Todo

- [ ] Allow flags to be passed to `tcpdump`
- [ ] Port the [logic to ksniff to allow multiple pods / deployment / daemonset
      to be packet captured](https://github.com/eldadru/ksniff/issues/104)


## Credits

* Inspired by [ksniff](https://github.com/eldadru/ksniff) but took a slight different approach

