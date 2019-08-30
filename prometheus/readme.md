##### 安装以及测试过程 相关的annotations为true的可不加

1. 准备prometheus.yml文件，并创建configmap，通过这样挂载到pod,方便后续更新

* 说明: etcd-key.pem etcd.pem rules.yml这里可以忽略先
* kubectl create configmap  -n monitoring prometheus-config --from-file=etcd-key.pem --from-file=etcd.pem  --from-file=prometheus.yml --from-file=rules.yml

2. 配置rbac认证，因为需要prometheus去访问kubernetes的相关信息 见prometheus-rbac.yaml

* 其中增加了对ingress的相关权限
* kubect apply -f prome-rbac.yaml

3. 部署prometheus，见prome-deploy.yaml

* 说明:--web.enable-lifecycle 需要添加，方便热加载配置文件,后续做一些测试会需要用到
* kubectl apply -f prome-deploy.yaml

4. 部署promtheus service，见prome-service.yaml

* kubectl apply -f prome-service.yaml

5. 部署prometheus ingress,见prome-ing.yaml

* kubectl apply -f prome-ing.yaml

6. 查看相关pod运行情况 见prometheus-pod-log.png

* kubectl get po -n monitoring |grep prome
* kubectl logs -n monitoring prometheus-74f95d7588-vd6qt