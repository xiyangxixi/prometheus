##### 全文参考:https://www.qikqiak.com/k8s-book/docs/59.%E8%87%AA%E5%AE%9A%E4%B9%89Prometheus%20Operator%20%E7%9B%91%E6%8E%A7%E9%A1%B9.html

##### 部署prometheus-operator

* prometheus-operator地址: git clone https://github.com/coreos/kube-prometheus.git
* 文件都在manifests里面

* 部署: kubectl apply -f manifests/

* grafana prometheus均用ingress来访问


##### 说一下未自带的监控

##### etcd监控

* 创建etcd证书相关的secret/configmap
* kubectl -n monitoring create secret generic etcd-certs --from-file=etcd-key.pem --from-file=etcd.pem --from-file=/etc/kubernetes/ssl/ca.pem
* 修改prometheus的部署文件，添加etcd-certs，见prometheus-prometheus.yaml,并部署
* 创建etcd相关的servicemonitor，见etcd-serviceMonitor.yaml
* 创建etcd相关的service，见etcd-service.yaml

##### service ingress cadvisor监控

* 创建相关的secret: kubectl create secret generic additional-configs --from-file=add.yaml  -n monitoring
* 修改prometheus的部署文件，见prometheus-prometheus.yaml,并部署
* 这里需要部署一下black-exporter
* 修改一下prometheus-clusterRole.yaml，见prmetheus-clusterRole.yaml，并部署


##### 持久化 使用storageclass
