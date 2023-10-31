# A la fois deployment
## Overview
We are using [Yandex Cloud](https://cloud.yandex.ru/) as our cloud provider.
This repo is an example for deploying A la fois to k8s cluster.
For now we use managed Kafka cluster, mongo and redis.

### Architecrute
![](/img/a-la-fois_architecture.png)
// TODO

## [WIP] Setup
<!-- 1. Install Dapr to a Kubernetes cluster. 

    ```shell
    dapr init -k
    ```
    More info:
    https://docs.dapr.io/operations/hosting/kubernetes/kubernetes-deploy/

2. Create a Secret
    ```shell
    cp example.secret.yaml secret.yaml
    ```
    
    Set values to `secret.yaml`
    ```yaml
    apiVersion: v1
    kind: Secret
    metadata:
      name: mongodb-secret
    type: Opaque
    data:
      username: <NONGO_USERNAME>
      password: <MONGO_PASSWORD>
      uri: <MONGO_URI> # https://www.mongodb.com/docs/manual/reference/connection-string/ 
    
    
    ---
    
    apiVersion: v1
    kind: Secret
    metadata: 
      name: redis-secret
    type: Opaque
    data:
      redis-password: <REDIS_PASSWORD>
    
    
    ---
    
    apiVersion: v1
    kind: Secret
    metadata:
      name: kafka-secret
    type: Opaque
    data:
      username: <KAFKA_USERNAME>
      password: <KAFKA_PASSWORD>
    ```
    
    ```shell
    kubectl apply -f secter.yaml
    ```
3. Create a config map
    Set your kafka config and apply ConfigMap
        
    ```shell
    kubectl apply -f configMap.yaml
    ```
    
4. Create a Redis deployment
    ```shell
    kubectl apply -f redis.yaml
    ```
5. Create a Mongodb deployment
    ```shell
    kubectl apply -f mongo.yaml
    ```
6. Create Dapr state store component.

    The state store is needed for actors
    ```shell
    kubectl apply -f stateStore.yaml
    ```
7. Create deployments for messageProxy and docHandler
    ```shell
    kubectl apply -f messageProxy.yaml
    kubectl apply -f docHandler.yaml
    ```

For now we use a simple external service to balance traffic. You cat find an ip of the service by executing `kubectl get services`
```shell
➜  a-la-fois git:(main) kubectl get services
NAME                    TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                               AGE
dapr-api                ClusterIP      10.96.156.13    <none>          80/TCP                                44h
dapr-dashboard          ClusterIP      10.96.184.27    <none>          8080/TCP                              44h
dapr-placement-server   ClusterIP      None            <none>          50005/TCP,8201/TCP                    44h
dapr-sentry             ClusterIP      10.96.137.44    <none>          80/TCP                                44h
dapr-sidecar-injector   ClusterIP      10.96.141.175   <none>          443/TCP                               44h
dapr-webhook            ClusterIP      10.96.221.173   <none>          443/TCP                               44h
doc-handler-dapr        ClusterIP      None            <none>          80/TCP,50001/TCP,50002/TCP,9090/TCP   38h
kubernetes              ClusterIP      10.96.128.1     <none>          443/TCP                               44h
message-proxy-dapr      ClusterIP      None            <none>          80/TCP,50001/TCP,50002/TCP,9090/TCP   44h
message-proxy-service   LoadBalancer   10.96.148.93    130.193.53.53   3000:30000/TCP                        37h
mongodb-service         ClusterIP      10.96.184.56    <none>          27017/TCP                             44h
redis-service           ClusterIP      10.96.208.1     <none>          6379/TCP                              44h
```
Our message proxy service external IP is `130.193.53.53`
Use this IP in the docClient to connect to A la fois.
 -->
