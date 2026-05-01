# argocd-dad-jokes
Demo for deploying Soyokaze-42/CIS467-SP26-dad-jokes-app with ArgoCD

Prerequisites:
1) Install (OpenShift Local (crc))[https://developers.redhat.com/products/openshift-local]
2) Configure OpenShift Local with enough resources and start it
```
crc config set cpus 8
crc config set memory  12288
crc config set disk-size 40
crc setup
crc start
```
3) When it is ready, log into the webapp with the kubeadm credentials you get after starting crc.
4) Setup oc and log in on the CLI with the developer credentials (instructions for this are also provided when crc starts)
5) Install the CloudNativePG Operator from the Ecosystem -> Software Catalog menu
6) Install the ArgoCD Operator from the same Catalog
7) create the argocd namespace `oc new-project argocd-demo`
8) create and configure the ArgoCD server `curl -s https://raw.githubusercontent.com/Soyokaze-42/argocd-dad-jokes/refs/heads/main/argocd-server.yaml | oc apply -f -`
9) create the ArgoCD Application `curl -s https://raw.githubusercontent.com/Soyokaze-42/argocd-dad-jokes/refs/heads/main/dad-jokes-app.yaml | oc apply -f -`

All the resources to deploy this app are in the resources directory. This is referenced in the dad-jokes-app.yaml ArgoCD Application manifest.

