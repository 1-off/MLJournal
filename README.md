# MLJournal

## installing Kuberflow-light
```bash
snap list
sudo snap install microk8s --channel=1.22/stable --classic
sudo snap install juju --classic
sudo usermod -a -G microk8s oneoff
sudo chown -f -R oneoff ~./kube
sudo reboot now

alias kubectl='microk8s kubectl'
microk8s enable dns storage gpu istio
microk8s config > ~/.kube/config

juju add-k8s myk8s
juju clouds

juju bootstrap myk8s my-controller
kubectl get po -A
kubectl get namespace

juju add-model kubeflow
juju models
kubectl get namespace
juju deploy kubeflow-lite --trust

juju status --color  //window 1
watch -c kubectl get po -n kubeflow //window 2

juju config dex-auth static-username=admin
juju config dex-auth static-password=thisisapassword

microk8s enable metallb
microk8s enable metallb:10.64.140.43-10.64.140.49

kubectl get services -n kubeflow

microk8s kubectl patch role -n kubeflow istio-ingressgateway-operator -p '{"apiVersion":"rbac.authorization.k8s.io/v1","kind":"Role","metadata":{"name":"istio-ingressgateway-operator"},"rules":[{"apiGroups":["*"],"resources":["*"],"verbs":["*"]}]}'

juju config dex-auth public-url=http://<URL>
juju config oidc-gatekeeper public-url=http://<URL>
```
## Issues
- https://github.com/canonical/bundle-kubeflow/issues/509

## Fixes
```
rm -rf .local/share/juju
sudo snap remove microk8s --purge
sudo snap remove juju --purge
sudo snap remove microk8s --purge; juju unregister -y <controller-name>
```
