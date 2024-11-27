# lukecodewalker's helm charts


## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

helm repo add luke-codewalker https://luke-codewalker.github.io/helm-charts

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages. You can then run
`helm search repo luke-codewalker` to see the charts.

## Creating a secret

- have `kubeseal` and `kubectl` installed and ready to go
- generate a secret e.g.
  `kubectl create secret generic database-url --dry-run=client -o yaml --from-literal=DATABASE_URL=<base64-string>`
- encrypt it using the sealed secrets controller in your target cluster e.g.
  `kubeseal --controller-name sealed-secrets --controller-namespace sealed-secrets -o yaml <secret.yaml >sealed-secret.yaml`
- commit the file and use it in your templates
