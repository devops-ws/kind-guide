# kind-guide

```shell
kind create cluster --image 10.121.218.184:30002/cache/kindest/node:v1.25.3 --config kind.yaml
```

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
containerdConfigPatches:
- |-
  version = 2
  [plugins."io.containerd.grpc.v1.cri".registry]
    [plugins."io.containerd.grpc.v1.cri".registry.mirrors]
      [plugins."io.containerd.grpc.v1.cri".registry.mirrors."quay.io"]
        endpoint = ["http://10.121.218.184:30002/v2/quay.io"]
  [plugins."io.containerd.grpc.v1.cri".registry.configs."10.121.218.184:30002".tls]
    insecure_skip_verify = true
  [plugins."io.containerd.grpc.v1.cri".registry.configs]
    [plugins."io.containerd.grpc.v1.cri".registry.configs."10.121.218.184:30002".auth]
      username = "robot_readonly"
      password = 'npcCnfZicoeZTupZnX39ew9cfIvldyZV'
```
