# About 
Kustomize configs for OpenShift types like BuildConfigs, Imagestreams, DeploymentConfigs

### How to use it with your openshift objects

1. Download and copy over the [kustomizeconfig](../master/kustomizeconfig) directory into your `$TEMPLATE_HOME` directory.
2. Update your kustomization.yaml to include all the `configurations` in [kustomization.yaml](../master/kustomization.yaml)


Note: `kustomize` doesn't allow specification of remote urls for `configurations` in `kustomization.yaml`

### Examples
- https://github.com/sbose78/nodejs-ex/tree/e025e8f3b6bcac6475a3319ab3995ef3eb871d33/deploy/template/nodejs-ex-k
