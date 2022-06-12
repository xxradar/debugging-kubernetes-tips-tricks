### Find the containerID in kubernetes
```
containerid=$(kubectl get po www-demo -o json | jq -r '.status.containerStatuses[0].containerID')
echo ${containerid/docker:\/\//}
```
### Find pid in Docker
```
pid=$(docker inspect -f '{{.State.Pid}}' ${containerid/docker:\/\//})
```
### Find pid in Containerd
```
sudo crictl inspect 0b9c1ba3417a100e0fb41add7eddb1c449065e3fe77de37b5636a5be591693fc | jq -r .info.pid
```
### Find process 
```
ps aux | grep $pid
```
