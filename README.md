# cuter
``` sh
kind create cluster --config ../cilium-kind/config.yaml 
kind create cluster --config <(cat <<EOF
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
  - role: worker
  - role: worker
networking:
  disableDefaultCNI: true
EOF
)
helm install cilium isovalent/cilium -n kube-system         
export GITHUB_TOKEN=<INSERT PAT>
flux bootstrap github --owner=rajsinghtech --repository=cuter --path=clusters/kind
```