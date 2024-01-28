# jenkins-app

## Docker Compose で起動する場合

```bash
$ docker compose up -d
```

## k8s で Jenkins を起動する場合

### Kind 起動

```bash
$ kind create cluster --config k8s/multi-node.yaml
```

### デプロイ

```bash
$ kubectl apply -f ./k8s/jenkins
```

### ポートフォワード

```bash
$ kubectl --namespace default port-forward svc/jenkins 8080:8080
```

## helm で Jenkins を起動する場合

### Kind 起動

```bash
$ kind create cluster --config k8s/multi-node.yaml
```

## jenkins インストール

```bash
$ helm install jenkins jenkins/jenkins
```

### パスワード取得

```bash
$ kubectl exec --namespace default -it svc/jenkins -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo
```

### ポートフォワード

```bash
$ kubectl --namespace default port-forward svc/jenkins 8080:8080
```

### ログイン

```
username:admin
password:
```

### アンインストール

```bash
$ helm delete jenkins
```

### リポジトリ一覧取得

```bash
$ helm repo list
```

### リポジトリ追加

```bash
$ helm repo add XXX
```

### リポジトリ削除

```bash
$ helm repo remove XXX
```
