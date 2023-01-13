# MLJournal

## installing Kuberflow-light
```bash
sudo snap install microk8s --classic --channel=1.22/stable
sudo snap install juju --classic

sudo microk8s enable gpu dns storage ingress istio metallb:10.64.140.43-10.64.140.49 
sudo microk8s config > ~/.kube/config

juju add-k8s myk8s
juju bootstrap myk8s my-controller
juju add-model kubeflow
juju deploy kubeflow-lite --trust

---- wait ---- check status of juju and microk8s (5-10 min)
juju status --color  //window 1
watch -c sudo microk8s kubectl get po -n kubeflow //window 2
---------------

sudo microk8s kubectl get svc -A | grep istio
juju config dex-auth public-url=http://<IP>.nip.io
juju config oidc-gatekeeper public-url=http://<IP>.nip.io

juju config dex-auth static-username=admin
juju config dex-auth static-password=thisisapassword

#check Juju
juju models
juju clouds

#check microk8s
sudo microk8s kubectl get po -A
sudo microk8s kubectl get namespace
sudo microk8s kubectl get services -n kubeflow | grep istio-ingressgataway-workload
sudo microk8s kubectl get svc -A | grep istio
```
## Issues
- https://github.com/canonical/bundle-kubeflow/issues/509
- https://bleepcoder.com/kubeflow/748548648/cannot-access-the-kubeflow-dashboard

## Fixes
```
rm -rf .local/share/juju
sudo snap remove microk8s --purge
sudo snap remove juju --purge
sudo snap remove microk8s --purge; juju unregister -y <controller-name>
```
## What-is
- [nip.io](https://cluedin-io.github.io/Home/faq/nip/)
