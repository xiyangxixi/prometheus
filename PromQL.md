* rate topk delta predict_linear 
* PromQL支持使用=和!=两种完全匹配模式
* label=~regx label!~regx 多个表达式之间使用|进行分离 http_requests_total{environment=~"staging|testing|development",method!="GET"}
* http_request_total{} offset 5m   http_request_total{}[1d] offset 1d
* sum avg 
* + - * / % ^
* (node_memory_bytes_total - node_memory_free_bytes_total) / node_memory_bytes_total > 0.95
* == != > < >= =>
* http_requests_total > bool 1000 返回真实bool值
* and or unless
* irate是PromQL中的内置函数，用于计算区间向量中时间序列每秒的即时增长率
* 使用on(label list)或者ignoring(label list）来修改便签的匹配行为
* group_left或者group_right来确定哪一个向量具有更高的基数
* sum min max avg stddev stdvar count count_values bottomk topk quantile without by
* increase(node_cpu[2m]) / 120   rate(node_cpu[2m]) irate(node_cpu[2m])
* predict_linear(node_filesystem_free{job="node"}[2h], 4 * 3600) < 0 预测磁盘在4小时后是否被占满
* label_replace(up, "host", "$1", "instance",  "(.*):.*") 通过label_replace标签为时间序列添加额外的标签
* 


* label_join函数，该函数可以将时间序列中v多个标签src_label的值，通过separator作为连接符写入到一个新的标签dst_label中
* label_join(v instant-vector, dst_label string, separator string, src_label_1 string, src_label_2 string, ...)


##### 4个黄金指标

* 延迟：服务请求所需时间
* 通讯量：监控当前系统的流量，用于衡量服务的容量需求
* 错误：监控当前系统所有发生的错误请求，衡量当前系统错误发生的速率
* 饱和度：衡量当前服务的饱和度