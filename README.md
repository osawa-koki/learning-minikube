# learning-minikube

🔊🔊🔊 Minikubeを使ってみる！  

## 実行方法

DevContainerに入り、以下のコマンドを実行します。  

```shell
minikube start --driver=docker --kubernetes-version=v1.28.0
kubectl create deployment nginx-test --image=nginx:1.25
kubectl expose deployment nginx-test --type=NodePort --port=80
kubectl get pods
kubectl get services
curl $(minikube service nginx-test --url)
```
