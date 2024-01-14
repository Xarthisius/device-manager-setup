# device-manager-setup
Contains yaml files to setup /dev/fuse device mount in kubernetes

### Example

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: fuse-test
  labels:
    app: fuse-test
spec:
  replicas: 1
  selector:
    matchLabels:
      name: fuse-test
  template:
    metadata:
      labels:
        name: fuse-test
    spec:
      containers:
      - name: fuse-test
        image: yufenkuo/test:v8
        securityContext:
          privileged: false
          capabilities:
            add: ["SYS_ADMIN"]
        resources:
          limits:
            smarter-devices/fuse: 1
            memory: 2048Mi
          requests:
            smarter-devices/fuse: 1
            cpu: 1
            memory: 1024Mi
```
