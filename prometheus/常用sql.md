* sum(up{job="kubernetes-cadvisor"}) by(job,instance)
* sum(up{job="kubernetes-pods",kubernetes_namespace=~"monitoring|kube-system",instance!~"(.*):53|(.*):80|(.*):8443|(.*):44134|(.*):10053"}) by(app,instance,job,kubernetes_namespace)
* sum by(app, instance, job, kubernetes_namespace) (up{instance!~"(.*):53|(.*):80|(.*):8443|(.*):44134|(.*):10053"})

* 