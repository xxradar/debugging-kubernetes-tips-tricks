### Find the containerid in kubernetes
```
containerid=$(kubectl get po www-demo -o json | jq -r '.status.containerStatuses[0].containerID')
echo $containerid
```
### Docker
```
pid=$(docker inspect -f '{{.State.Pid}}' ${containerid/docker:\/\//})
```
### Containerd
```
crictl inspect ${containerid/docker:\/\//}
```
### Find process 
```
ps aux | grep $pid
```
