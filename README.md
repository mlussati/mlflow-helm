# mlflow-helm
Este repositório é para hospedar kubernetes manifests do helm

`helm install [RELEASE_NAME] <chart/path>`

Obtenha o URL do aplicativo executando estes comandos:
  ```
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=mlflow,app.kubernetes.io/instance=kedro-mlflow" -o jsonpath="{.items[0].metadata.name}")
  
  export CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  
  echo "Visit http://127.0.0.1:8080 to use your application"
  
  kubectl --namespace default port-forward $POD_NAME 8080:$CONTAINER_PORT
  ```
