Next, we will deploy a set of monitoring and alarming services, and learn the common monitoring metrics and alarming rules in cloud services in the process.

1. Deploy vmoperator.
    ```
    kubectl apply -f 2-deploy-observability-service/2-1-vmoperator/crd.yaml
    kubectl apply -f 2-deploy-observability-service/2-1-vmoperator/rbac.yaml
    kubectl apply -f 2-deploy-observability-service/2-2-vmcluster/vmcluster.yaml
    ```
2. Deploy vmcluster to provide metrics read and write services.
    ```
    kubectl apply -f 2-deploy-observability-service/2-2-vmcluster/vmcluster.yaml
    ```
3. Deploy vmagent with monitoring metrics.
    ```
    kubectl apply -f 2-deploy-observability-service/2-3-vmagent/exporter.yaml
    kubectl apply -f 2-deploy-observability-service/2-3-vmagent/scrapes.yaml
    kubectl apply -f 2-deploy-observability-service/2-3-vmagent/vmagent.yaml
    ```
4. Deploy vmalert with alert rules.
    ```
    kubectl apply -f 2-deploy-observability-service/2-4-vmalert/rule.yaml
    kubectl apply -f 2-deploy-observability-service/2-4-vmalert/vmalert.yaml
    ```