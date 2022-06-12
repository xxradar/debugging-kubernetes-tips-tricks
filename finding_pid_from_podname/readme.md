### Find the containerID in kubernetes
```
containerid=$(kubectl get po www-demo -o json | jq -r '.status.containerStatuses[0].containerID')
echo ${containerid/docker:\/\//}. #docker
echo ${containerid/containerd:\/\//} #containerd
```
### Find pid in Docker
```
pid=$(docker inspect -f '{{.State.Pid}}' ##docker_container_id## )
```
### Find pid in Containerd
```
sudo crictl inspect ##containerd_container_id## | jq -r .info.pid
```
### Find process 
```
ps aux | grep $pid
```
