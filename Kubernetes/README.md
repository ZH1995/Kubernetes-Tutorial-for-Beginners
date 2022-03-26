#### 1. 启动单个实例

```bash
kubectl run nginx --image=nginx:1.10.0
```

#### 2. 获取pods

```bash
kubectl get pods
```

#### 3. 暴露nginx

```bash
kubectl expose deployment nginx --port 80 --type LoadBalancer
```

#### 4. 服务列表

```bash
kubectl get services
```

#### 5. 创建pod

```bash
kubectl create -f pods/monolith.yaml
```

查看pod信息

```bash
kubectl describe pods monolith
```

#### 6. pod命令

端口转发

```bash
kubectl port-forwarding monolith 10080:80
```

查看日志

```bash
kubectl logs monolith
```

进入pod内查看日志

```bash
kubectl exec monolith --stdin --tty -c monolith /bin/sh
```

#### 7. Service

集群内pod不断新增/消亡，所以单个pod的ip不稳定，多个pod以Service对外提供稳定服务。