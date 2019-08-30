##### alertmanager安装与测试

1. 创建配置文件 见alert-conf.yaml

* kubectl apply -f alert-conf.yaml

2. 部署alertmanager,见alert-deploy.yaml

* kubectl apply -f alert-deploy.yaml

3. 部署alert service，见alert-service.yaml

* kubectl apply -f alert-service.yaml

4. prometheus接入alertmanager，见prometheus.yml 这里添加了告警规则文件，放到了prometheus pod的/etc/prometheus下

* 说明: etcd-key.pem etcd.pem rules.yml这里可以忽略先
* kubectl create configmap  -n monitoring prometheus-config --from-file=etcd-key.pem --from-file=etcd.pem  --from-file=prometheus.yml --from-file=rules.yml
* 重新加载prometheus配置: curl -X POST "http://prometheus_service_ip:9090/-/reload"

5. 在protheus中查看告警规则，见prometheus-alert-1.png

6. 告警邮件以及resolve邮件,见firing.png和resoled.png