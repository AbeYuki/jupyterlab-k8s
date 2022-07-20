# jupyterlab-k8s
jupyterlab with kubernetes


# Example
環境ごとに用意されている kustomize があるディレクトリに移動  
```
cd overlay/dev/
```
個人のコンテナレジストリを利用する場合は docker-registry.json を作成し、kustomization.yaml の images/newName を変更してください。  
```
username=Jupyterlab
password=Password
auth=$(echo -n "${username}:${password}" | base64)
```
```
cat <<EOF> docker-registry.json
{"auths":{"registry.gitlab.com":{"username":"${username}","password":"${password}","auth":"${auth}"}}}
EOF
```
デプロイ  
```
kubectl apply -k ./
```