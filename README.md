# About 
Kustomize [Transformer Configurations](https://github.com/sbose78/openshift-kustomizeconfigs/tree/master/kustomizeconfig) for OpenShift types namely, BuildConfigs, Imagestreams and DeploymentConfigs.


### How to use it with your openshift objects

1. Download and copy over the [kustomizeconfig](../master/kustomizeconfig) directory into `$TEMPLATE_HOME/kustomizeconfig`.
2. Update your kustomization.yaml to include all the `configurations` in [kustomization.yaml](../master/kustomization.yaml)


Note: `kustomize` doesn't allow specification of remote urls for `configurations` in `kustomization.yaml`

## Usage

Assuming the kustomize workspace looks like:

```
├── kustomization.yaml
├── overlays
│   └── dev
│       ├── kustomization.yaml
│       └── service_port.yaml
└── resources
    ├── _helpers.tpl
    ├── buildconfig.yaml
    ├── deployment.yaml
    ├── imagestream.yaml
    ├── route.yaml
    └── service.yaml

```

To add a transformer config to custom OpenShift types like BuildConfig, we need to convey to Kustomize where in the spec lies the `image`. 

Similarly, we need to convey the path to the image specification in a DeploymentConfig and in an Imagestream.

The configuratiom for ImageStreams, BuildConfigs and DeploymentConfigs are maintained in [openshift-kustomizeconfigs/kustomizeconfig](https://github.com/sbose78/openshift-kustomizeconfigs/tree/master/kustomizeconfig). They can be used of the box by copying over the directory into your Kustomize workspace as shown below.

```
├── kustomization.yaml
├── kustomizeconfig
│   ├── buildconfig.yaml
│   ├── deploymentconfig.yaml
│   └── imagestream.yaml
├── overlays
│   └── dev
│       ├── buildconfig.yaml
│       ├── kustomization.yaml
│       └── service_port.yaml
└── resources
    ├── buildconfig.yaml
    ├── deployment.yaml
    ├── imagestream.yaml
    ├── route.yaml
    └── service.yaml
```

To enable it, add the following to your base kustomization.yaml

```
configurations: 
  - kustomizeconfig/imagestream.yaml
  - kustomizeconfig/buildconfig.yaml
  - kustomizeconfig/deploymentconfig.yaml
```

Sample usage could be found in 
https://github.com/sbose78/nodejs-ex