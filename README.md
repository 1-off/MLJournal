# MLJournal

## installing Kuberflow-light
```bash
snap list
sudo snap install microk8s --classic
sudo snap install juju --classic
sudo usermod -a -G microk8s ubuntu
sudo chown -f -R ubuntu ~./kube
reboot now or exit

alias kubectl='microk8s kubectl'
microk8s enable dns storage
kubectl get po -A
microk8s config > ~/.kube/config

juju add-k8s myk8s
juju bootstrap myk8s my-controller
kubectl get namespace
juju add-model kuberflow
juju model
kubectl get namespace
juju deploy kubeflow-lite

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
