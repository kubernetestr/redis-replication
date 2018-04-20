## A replicated Redis setup running in GKE with GCE persistent storage and autoscaling, implemented with StatefulSet's.

### First, create a namespace for our replicaset.
- `kubectl create namespace redis-rs`

### Then create a persistent volume class:
- `kubectl apply -f 01-hdd.yaml`

### Then create the first master and sentinel:
- `kubectl apply -f 02-redis-master.yaml`

### Wait for master pod to be ready...

### Then create the services for redis and sentinel:
- `kubectl apply -f 03-redis-service.yaml`
- `kubectl apply -f 04-redis-sentinel-service.yaml`

### Then, first create a statefulset for redis...
- `kubectl apply -f 05-redis-statefulset.yaml`

### ...and then another one for redis sentinel:
- `kubectl apply -f 06-redis-sentinel-statefulset.yaml`

### Lastly, create the autoscaler:
- `kubectl apply -f 07-autoscaler.yaml`

### Scale up our replication:
- `kubectl scale statefulset --namespace=redis-rs redis --replicas=3`
- `kubectl scale statefulset --namespace=redis-rs redis-sentinel --replicas=3`

### Delete the master pod:
- `kubectl delete pods --namespace=redis-common redis-master`
