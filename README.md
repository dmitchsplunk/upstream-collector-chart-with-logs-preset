# upstream-collector-chart-with-logs-preset

This example shows how to deploy the OpenTelemetry collector in a Kubernetes environment using the OpenTelemetry Collector Helm Chart <https://opentelemetry.io/docs/kubernetes/helm/collector/>. 

The values.yaml file includes: 

1) Presets for logCollection, kubernetesAttributes, kubeletMetrics, kubernetesEvents, and hostMetrics
2) Exporters to send metrics and traces to Splunk Observability Cloud
3) Exporters to send logs to AWS CloudWatch Logs and Splunk Platform

Edit configmap.yaml and secret.yaml with the specific parameters for your environment. 

Then use the following commands to deploy the chart: 

kubectl apply -f ./configmap.yaml
kubectl apply -f ./secret.yaml

helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts

helm install my-opentelemetry-collector open-telemetry/opentelemetry-collector \
   -f ./values.yaml
