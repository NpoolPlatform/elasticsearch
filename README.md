# elasticsearch

elasticsearch for fulltext search or tracing data store

## Install ECK

### Helm
[Helm install](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-install-helm.html#k8s-install-helm-global)

first read [ECK Config](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-operator-config.html), and disable fllow features

+ disable-telemetry

Add the Elastic Helm charts repo:

> helm repo add elastic https://helm.elastic.co
> helm repo update

Install it:

> helm install elastic-operator elastic/eck-operator -n elastic-system --create-namespace

## Install ES

> kubectl apply -f k8s/elasticsearch.yaml

---

## 集群规模
+ client * 2
+ data * 3(2G)
+ master * 3(1G)
## Jenkins

Jenkins UI 涉及的环境变量和可选值

| 环境变量      | 值   | 说明 |
|:--------------|:-----|:-----|
| BRANCH_NAME   |      |      |
| DEPLOY_TARGET | true |      |

---

## 依赖的资源

+ [certificate](https://www.elastic.co/guide/en/cloud-on-k8s/1.1/k8s_manage_the_webhook_certificate_with_cert_manager.html)
+ storage
    依赖的 pvc name **elastic-pvc** 大小 **3*50G**
## 拓展

[linkerd](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-service-mesh-linkerd.html)
