# label-studio-helm

An experimental Label Studio community edition helm chart building and release hosting repository.

**DO NOT USE THIS FOR PRODUCTION!**

## Default login

Username: `admin@example.com`
Password: `password123`

## Useful commands

You need both `kubectl` and `helm` commands, and an existing k8s that you already have access to,
with a valid Ingress controller set-up.

The following was tested using `kind` to create a cluster to allow Ingress on local set-up:
<https://kind.sigs.k8s.io/docs/user/ingress/#create-cluster>, followed by the two NGINX commands:
<https://kind.sigs.k8s.io/docs/user/ingress/#ingress-nginx>.

Run the following commands to get the `label-studio` set up:

```bash
helm package . -d dist/  # Creates label-studio-x.y.z.tgz
helm repo add bitnami https://charts.bitnami.com/bitnami  # For postgresql
helm dependency build    # Creates / updates charts/postgresql
helm repo index .        # Creates / updates index.yaml
helm upgrade --install --set-json 'ingress.path="/label-studio"' label-studio .
```

Assuming your Ingress controller hosts at port 80, you should be able to see label-studio being
hosted at <http://localhost:80/label-studio>.
