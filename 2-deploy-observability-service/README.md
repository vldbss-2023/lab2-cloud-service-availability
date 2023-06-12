Next, we will deploy a set of monitoring and alarming services, and learn the common monitoring metrics and alarming rules in cloud services in the process.

1. Deploy vmoperator.
    ```bash
    $ kubectl apply -f 2-deploy-observability-service/2-1-vmoperator/crd.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-1-vmoperator/rbac.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-1-vmoperator/manager.yaml
    ```
2. Deploy vmcluster to provide metrics read and write services.
    ```bash
    $ kubectl apply -f 2-deploy-observability-service/2-2-vmcluster/vmcluster.yaml
    $ kubectl get pod -n observability
    NAME                                  READY   STATUS    RESTARTS   AGE
    vminsert-vmcluster-7c78fc7bd8-rmjpj   1/1     Running   0          2m9s
    vmselect-vmcluster-0                  1/1     Running   0          2m9s
    vmstorage-vmcluster-0                 1/1     Running   0          2m9s
    ```
3. Deploy vmagent with monitoring metrics.
    ```bash
    $ kubectl apply -f 2-deploy-observability-service/2-3-vmagent/exporter.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-3-vmagent/scrapes.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-3-vmagent/vmagent.yaml
   
    # View the metrics we collected
    $ kubectl port-forward svc/vmselect-vmcluster 8481:8481
    http://127.0.0.1:8481/select/0:0/vmui/?#/cardinality
    ```
4. Deploy vmalert with alert rules.
    ```bash
    $ kubectl apply -f 2-deploy-observability-service/2-4-vmalert/rule.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-4-vmalert/alertmanager.yaml
    $ kubectl apply -f 2-deploy-observability-service/2-4-vmalert/vmalert.yaml
    # View the alerts
    $ kubectl port-forward svc/vmalertmanager-default-alertmanager 9093:9093
    http://127.0.0.1:9093/#/alerts

    ```