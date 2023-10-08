# Additional manual steps

## Cluster Setup

```bash
# new first server node
curl -sfL https://get.k3s.io | K3S_TOKEN=<shared-token> sh -s - server \
	--cluster-init \
  --cluster-cidr="10.243.0.0/16" \
	--flannel-backend=wireguard-native \
	--write-kubeconfig-mode=644 \
  --disable local-storage \
  --node-name="$(hostname -f)" \
  --kube-controller-manager-arg="bind-address=0.0.0.0" \
  --kube-proxy-arg="metrics-bind-address=0.0.0.0" \
  --kube-scheduler-arg="bind-address=0.0.0.0" 

# second server node
curl -sfL https://get.k3s.io | K3S_TOKEN=<shared-token> sh -s - server \
	--server https://<server-ip>:6443 \
  --cluster-cidr="10.243.0.0/16" \
	--flannel-backend=wireguard-native \
	--write-kubeconfig-mode=644 \
  --disable local-storage \
  --node-name="$(hostname -f)" \
  --kube-controller-manager-arg="bind-address=0.0.0.0" \
  --kube-proxy-arg="metrics-bind-address=0.0.0.0" \
  --kube-scheduler-arg="bind-address=0.0.0.0" 
```
