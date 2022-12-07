# label-studio-helm

An experimental Label Studio community edition helm chart building and release hosting repository.

**DO NOT USE THIS FOR PRODUCTION!**

## Default login

Username: `admin@example.com`
Password: `password123`

## Useful commands

```bash
helm package . -d dist/  # Creates label-studio-x.y.z.tgz
helm dependency build    # Creates / updates charts/postgresql
helm repo index .        # Creates / updates index.yaml
helm upgrade --install --set-json 'ingress.path="/label-studio"' label-studio .
```
