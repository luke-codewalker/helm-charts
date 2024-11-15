# Creating a secret

- have `kubeseal` and `kubectl` installed and ready to go
- generate a secret e.g.
  `kubectl create secret generic database-url --dry-run=client -o yaml --from-literal=DATABASE_URL=<base64-string>`
- encrypt it using the sealed secrets controller in your target cluster e.g.
  `kubeseal --controller-name sealed-secrets --controller-namespace sealed-secrets -o yaml <secret.yaml >sealed-secret.yaml`
- commit the file and use it in your templates
