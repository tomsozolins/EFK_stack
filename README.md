# EFK stack

## DEPLOY ELASTIC ECK OPERATOR
#### Source: https://www.elastic.co/guide/en/cloud-on-k8s/1.6/k8s-deploy-eck.html

```
# kubectl apply -f all-in-one.yaml
```

#### Check status:
```
# kubectl -n elastic-system logs -f statefulset.apps/elastic-operator
```

## DEPLOY ELASTICSEARCH CLUSTER
#### Source: https://www.elastic.co/guide/en/cloud-on-k8s/1.6/k8s-deploy-elasticsearch.html

```
# kubectl apply -f elasticsearch.yaml
```

#### Check status:
```
# kubectl get elasticsearch
# kubectl get pods --selector='elasticsearch.k8s.elastic.co/cluster-name=quickstart'
# kubectl logs -f quickstart-es-default-0
# kubectl get service quickstart-es-http
```
#### Get elastic user password:
```
# kubectl get secret quickstart-es-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode; echo
```

## DEPLOY KIBANA
#### Source: https://www.elastic.co/guide/en/cloud-on-k8s/1.6/k8s-deploy-kibana.html

```
# kubectl apply -f kibana.yaml
```
#### Check status:
```
# kubectl get kibana
# kubectl get pod --selector='kibana.k8s.elastic.co/name=quickstart'
# kubectl get service quickstart-kb-http
```

## DEPLOY FLUENTBIT
#### Source: https://gist.github.com/egernst/d8f20021db724ba831a2552ba02027fe
```
# kubectl apply -f fluent-bit-role-sa.yaml
# kubectl apply -f fluent-bit-configmap.yaml
# kubectl apply -f fluent-bit-ds.yaml
```
