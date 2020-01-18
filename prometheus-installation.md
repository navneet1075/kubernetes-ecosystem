Prometheus installation and adding kube-state-metrics

1. Go to the page :https://github.com/helm/charts/tree/master/stable/prometheus
2. Use the prometheus/stable chart : helm install  stable/prometheus.
            PS: You might need to add helm repo.  
            Add using  :  helm repo add stable	https://kubernetes-charts.storage.googleapis.com
3. helm repo update

Read the notes carefully to get the things running.

NOTES:
* The Prometheus server can be accessed via port 80 on the following DNS name from within your cluster:
prom-local-prometheus-server.default.svc.cluster.local


        * Get the Prometheus server URL by running these commands in the same shell:
        * export POD_NAME=$(kubectl get pods --namespace default -l "app=prometheus,component=server" -o  jsonpath="{.items[0].metadata.name}")
        * kubectl --namespace default port-forward $POD_NAME 9090

* Port-forwarding to the port to directly access the prometheus.
* Better way is to create a Node Port Service and then access that.
** Installing kube-state-metrics for the Kubernetes objects stats/monitoring.
* Go to https://github.com/kubernetes/kube-state-metrics
* Git clone the repo.
* Install the objects from examples/standard  folder.
You can use grafana dashboard to see the pod , deployment overview . Use the existing dashboards already in the community.


