##### 安装以及测试过程  相关的annotations为true的可不加

1. 部署grafana,见grafana-deploy.yaml

* kubectl apply -f grafana-deploy.yaml

2. 部署grafana service,见grafana-service.yaml

* kubectl apply -f grafana-service.yaml

3. 部署grafana ingress,见grafana-ing.yaml

* kubectl apply -f grafana-ing.yaml

4. 查看pod 见grafana-po-log.png

* kubectl get po -n monitoring |grep grafana
* kubectl logs -n monitoring grafana*

5. 添加数据源 见grafana-prometheus-data.png