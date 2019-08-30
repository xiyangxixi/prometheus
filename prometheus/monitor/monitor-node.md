
##### 参考：https://prometheus.io/docs/prometheus/latest/configuration/configuration/#kubernetes_sd_config

* 监控node使用node-exporter
* 原本的端口替换成9100


1. 部署node-export,见prome-node.yaml

2. kubectl apply -f prome-node.yaml

3. 查看node-exporter的pod的状态

4. 利用服务发现去获取监控数据,见prometheus.yml中"kubernetes_node"

5. 重新创建prometheus的配置文件并加载

6. 查看结果，见prometheus-node.png