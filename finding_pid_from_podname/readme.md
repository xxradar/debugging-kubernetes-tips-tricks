### Find the containerID in kubernetes
```
containerid=$(kubectl get po www-demo -o json | jq -r '.status.containerStatuses[0].containerID')
echo $containerid
```
### Find pid in Docker
```
pid=$(docker inspect -f '{{.State.Pid}}' ${containerid/docker:\/\//})
```
### Find pid in Containerd
```
crictl inspect ${containerid/docker:\/\//}
```
### Find process 
```
ps aux | grep $pid
```
