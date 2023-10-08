# My flux cd cluster setup

## Initial cluster setup

Follow the steps outlined in [SETUP.md](./cluster/SETUP.md).

## Repo structure

After deploying [flux](https://fluxcd.io) on the cluster and pointing
it to this repo it should be able to create all the apps defined in the
[apps folder](./apps). For the sealed secrets the private key has to be deployed
on the cluster. Otherwise those secrets need to be recreated.
