k8s-static-code-analysis-demo
=============================

## 実行されるツールと役割

| ツール | 役割 |
| --- | --- |
| helm lint | HelmチャートのLintingツール。チャートが正しく構成されているかを検証し、エラーや警告を報告する。 |
| kubeconform | KubernetesリソースのYAMLファイルをスキーマに基づいて検証するツール。リソースがKubernetesの仕様に準拠しているか確認する。 |
| polaris | Kubernetesのリソースがベストプラクティスに準拠しているかどうかを評価する。 |
| pluto | Kubernetesリソースの非推奨APIを検出する。将来のバージョンで削除される可能性があるAPIの使用を特定する。 |
| trivy | Kubernetesのマニフェストの脆弱性や設定ミスを検出する。 |

## ローカル実行手順

### act

```console
% act pull_request --container-architecture linux/amd64
```

### helm lint

```console
% helm lint ./charts/mywebapp
```

### kubeconform

```console
% kubeconform --summary -output json ./charts/mywebapp
```

### polaris

```console
% polaris audit --only-show-failed-tests --helm-chart ./charts/mywebapp
```

### pluto

```console
% pluto detect-files -d ./charts/mywebapp
```

#### trivy

```console
% trivy config ./charts/mywebapp
```

## 参考

- https://v3-1-0.helm.sh/docs/helm/helm_lint/
- https://github.com/yannh/kubeconform
- https://polaris.docs.fairwinds.com/infrastructure-as-code/
- https://aquasecurity.github.io/trivy/v0.48/docs/coverage/iac/helm/
- https://github.com/helm/chart-testing
- https://github.com/helm/chart-testing-action
- https://github.com/helm/charts-repo-actions-demo
- https://helm.sh/docs/topics/charts/
- https://qiita.com/araryo/items/f072a0cca0b098f02e44
- https://zenn.dev/shunsuke_suzuki/articles/improve-cicd-with-github-comment
- https://polaris.docs.fairwinds.com/infrastructure-as-code/#running-in-a-ci-pipeline
- https://dev.to/aws-builders/improving-your-cicd-pipeline-helm-charts-security-scanning-with-trivy-and-github-actions-3315
- https://weblog.grimoh.net/entry/2022/01/02/100000
- https://qiita.com/suzuki0430/items/8b02f4d978ed11cd89b8
