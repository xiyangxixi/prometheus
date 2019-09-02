##### 在k8s上使用prometheus 当前未使用operator

##### 全文参考:https://www.qikqiak.com/k8s-book/docs/52.Prometheus%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8.html

##### 全文参考:https://github.com/yunlzheng/prometheus-book?from=singlemessage&isappinstalled=0

##### grafana 只做数据展示 告警由alertmanager来完成 相关的查询在prometheus进行


##### 准备工作

* 搭建好的kubernetes集群
* 搭建好的NFS服务器

##### 本次实验环境(不要在意ip的值，我瞎写的)




|序号|ip|角色或|
|--|--|--|
|1|1.1.1.1|master|
|2|1.1.1.2|master|
|3|1.1.1.3|node|
|4|1.1.1.4|node nfs|
|5|1.1.1.5|node harbor|