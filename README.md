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

## [生成访问用户](https://www.elastic.co/guide/en/cloud-on-k8s/master/k8s-users-and-roles.html)

```
docker run --rm docker.elastic.co/elasticsearch/elasticsearch:8.2.0 bash -c 'bin/elasticsearch-users useradd npooles -r superuser -p elastic12345679 ;cat config/users;cat config/users_roles'
```

注: 个人测试 **官方示例是错误的**, 使用上面的命令生成(注意修改账号和密码)

---

## 集群规模
+ client * 2
+ data * 3(2G+50G存储)
+ master * 3(1G+1G存储)

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
